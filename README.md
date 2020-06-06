# Debian-Install-Nginx
Debian 9/10 编译安装Nginx1.16.1，带第三方ngx_cache_purge / ngx_http_substitutions_filter_module

实际上，Nginx 的官方repo编译的nginx，已经把能加上的module全部都加上了，因此在一般情况下，建议使用nginx的官方repo来安装nginx. 但是如果说你想添加第三方的module，或者使用最新的openssl 的话，在或者更改一下nginx 的安装路径的话，就需要自己编译了. 此篇教程尽量按照nginx官方repo的configure来编译安装<code>openssl</code>/<code>ngx_cache_purge</code>/<code>ngx_http_substitutions_filter_module</code>
<br><br><br>
<b>安装</b><br>
建议在screen中执行，安装screen：
<pre>
apt-get install screen -y
screen -S nginx
</pre>

再执行Nginx一键安装脚本

<pre>
wget https://raw.githubusercontent.com/zunsking/Debian-Install-Nginx/master/Debian-install-nginx.sh
bash Debian-install-nginx.sh
</pre>
</br>
Nginx主配置文件目录：
<code>/etc/nginx/nginx.conf</code>
<br>
域名配置文件目录：
<code>/etc/nginx/vhost/</code>
<br>
默认静态文件目录：
<code>/etc/nginx/html/</code>
<br>
模块目录：
<code>/usr/lib/nginx/modules/</code>
<br>
日志目录：
<code>/var/log/nginx/access.log</code>
<code>/var/log/nginx/error.log</code>
<br><br><br>
管理命令：
<pre>service nginx (restart|reload|start|status|stop)</pre>
<br><br><br>
<b>已编译模块概览</b><br>
<pre>
./configure --prefix=/etc/nginx \
            --sbin-path=/usr/sbin/nginx \
	    --modules-path=/usr/lib/nginx/modules \
	    --conf-path=/etc/nginx/nginx.conf \
	    --error-log-path=/var/log/nginx/error.log \
	    --http-log-path=/var/log/nginx/access.log \
	    --pid-path=/var/run/nginx.pid \
	    --lock-path=/var/run/nginx.lock \
	    --http-client-body-temp-path=/var/cache/nginx/client_temp \
	    --http-proxy-temp-path=/var/cache/nginx/proxy_temp \
	    --http-fastcgi-temp-path=/var/cache/nginx/fastcgi_temp \
	    --http-uwsgi-temp-path=/var/cache/nginx/uwsgi_temp \
	    --http-scgi-temp-path=/var/cache/nginx/scgi_temp \
	    --user=nginx \
	    --group=nginx \
	    --with-compat \
	    --with-file-aio \
	    --with-threads \
	    --with-http_addition_module \
	    --with-http_auth_request_module \
	    --with-http_dav_module \
	    --with-http_flv_module \
	    --with-http_gunzip_module \
	    --with-http_gzip_static_module \
	    --with-http_mp4_module \
	    --with-http_random_index_module \
	    --with-http_realip_module \
	    --with-http_secure_link_module \
	    --with-http_slice_module \
	    --with-http_ssl_module \
	    --with-http_stub_status_module \
	    --with-http_sub_module \
	    --with-http_v2_module \
	    --with-mail \
	    --with-mail_ssl_module \
	    --with-stream \
	    --with-stream_realip_module \
	    --with-stream_ssl_module \
	    --with-stream_ssl_preread_module \	
	    --with-pcre=../pcre-8.43 \
	    --with-pcre-jit \
            --with-zlib=../zlib-1.2.11 \
	    --with-openssl=../openssl-1.1.1d \
	    --with-openssl-opt=no-nextprotoneg \			
	    --with-debug \			
	    --with-ngx_cache_purge \		
	    --with-ngx_http_substitutions
</pre>
<br><br><br>
<b>参考链接</b><br>
<li>https://www.iamhippo.com/2019-12/1196.html</li>
