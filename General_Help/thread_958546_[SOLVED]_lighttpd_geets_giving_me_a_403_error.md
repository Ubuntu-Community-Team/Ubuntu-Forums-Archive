---
title: "[SOLVED] lighttpd geets giving me a 403 error"
date: 2008-10-25
forum: General Help
---

### Post by Tak11 on 2008-10-25
i have my files in /home/tak.site/http/cgi-bin 
my root set in /homt/tak.site/http

when i try to access localhost/cgi-bin/index.pl 
or just localhost/cgi-bin/ it gives me a 403 error,

i chmod'ed everything to 777, still nothing,

lighttpd.conf
-----------------------------------------------------------------------------

# Debian lighttpd configuration file
# 

############ Options you really have to take care of ####################

## modules to load
# mod_access, mod_accesslog and mod_alias are loaded by default
# all other module should only be loaded if neccesary
# - saves some time
# - saves memory

server.modules              = ( 
            "mod_access",
            "mod_alias",
            "mod_accesslog",
            "mod_compress",
#           "mod_rewrite", 
#           "mod_redirect", 
	    "mod_status", 
#           "mod_evhost",
#           "mod_usertrack",
#           "mod_rrdtool",
#           "mod_webdav",
#           "mod_expire",
#           "mod_flv_streaming",
#           "mod_evasive",
	    "mod_cgi"
 )

## a static document-root, for virtual-hosting take look at the 
## server.virtual-* options
server.document-root       = "/home/tak.site/http/"

## where to send error-messages to
server.errorlog            = "/home/tak.site/error.log"

## files to check for if .../ is requested
index-file.names           = ( "index.pl" )


$HTTP["url"] =~ "^/cgi-bin/" {
index-file.names = ( "index.pl" )
}

## Use the "Content-Type" extended attribute to obtain mime type if possible
# mimetype.use-xattr = "enable"

#### accesslog module
accesslog.filename         = "/home/tak.site/access.log"

## deny access the file-extensions
#
# ~    is for backupfiles from vi, emacs, joe, ...
# .inc is often used for code includes which should in general not be part
#      of the document-root
url.access-deny            = ( "~", ".inc" )

##
# which extensions should not be handle via static-file transfer
#
# .php, .pl, .fcgi are most often handled by mod_fastcgi or mod_cgi
static-file.exclude-extensions = ( ".php", ".pl", ".fcgi" )

 
######### Options that are good to be but not neccesary to be changed #######

## bind to port (default: 80)
server.port               = 80

## bind to localhost only (default: all interfaces)
## server.bind                = "localhost"

## error-handler for status 404
#server.error-handler-404  = "/error-handler.html"
#server.error-handler-404  = "/error-handler.php"

## to help the rc.scripts
server.pid-file            = "/var/run/lighttpd.pid"

## 
## Format: <errorfile-prefix><status>.html
## -> ..../status-404.html for 'File not found'
#server.errorfile-prefix    = "/home/tak.site/"

## virtual directory listings
dir-listing.encoding        = "utf-8"
server.dir-listing          = "enable"

## send unhandled HTTP-header headers to error-log
#debug.dump-unknown-headers  = "enable"

### only root can use these options
#
# chroot() to directory (default: no chroot() )
#server.chroot            = "/"

## change uid to <uid> (default: don't care)
server.username            = "www-data"

## change uid to <uid> (default: don't care)
server.groupname           = "www-data"

#### compress module
compress.cache-dir          = "/var/cache/lighttpd/compress/"
compress.filetype           = ("text/plain", "text/html", "application/x-javascript", "text/css")

#### status module
 status.status-url = "/server-status"
 status.config-url = "/server-config"

#### url handling modules (rewrite, redirect, access)
# url.rewrite                 = ( "^/$"             => "/server-status" )
# url.redirect                = ( "^/wishlist/(.+)" => "http://www.123.org/$1" )

#
# define a pattern for the host url finding
# %% => % sign
# %0 => domain name + tld
# %1 => tld
# %2 => domain name without tld
# %3 => subdomain 1 name
# %4 => subdomain 2 name
#
# evhost.path-pattern = "/home/storage/dev/www/%3/htdocs/"

#### expire module
# expire.url                  = ( "/buggy/" => "access 2 hours", "/asdhas/" => "access plus 1 seconds 2 minutes")

#### rrdtool
# rrdtool.binary = "/usr/bin/rrdtool"
# rrdtool.db-name = "/var/www/lighttpd.rrd"


#### variable usage:
## variable name without "." is auto prefixed by "var." and becomes "var.bar"
#bar = 1
#var.mystring = "foo"

## integer add
#bar += 1
## string concat, with integer cast as string, result: "www.foo1.com"
#server.name = "www." + mystring + var.bar + ".com"
## array merge
#index-file.names = (foo + ".php") + index-file.names
#index-file.names += (foo + ".php")


#### external configuration files
## mimetype mapping


include_shell "/usr/share/lighttpd/create-mime.assign.pl"

## load enabled configuration files, 
include_shell "/usr/share/lighttpd/include-conf-enabled.pl"

#### handle Debian Policy Manual, Section 11.5. urls
### by default allow them only from localhost
### (This must come last due to #445459)
$HTTP["remoteip"] == "127.0.0.1" {
	alias.url += (
		"/doc/" => "/usr/share/doc/",
		"/images/" => "/usr/share/images/"
	)
	$HTTP["url"] =~ "^/doc/|^/images/" {
		dir-listing.activate = "enable"
	}
}

---

### Post by Mazin on 2008-10-26
I had the same problem, except I got it working with fastcgi using the guide here: [http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html](http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html)
(don't forget to "$ sudo /etc/init.d/lighttpd restart")

My problem was that vim automatically commented out the line I added to enable fastcgi.

---

### Post by Tak11 on 2008-10-27
Thanks, I eventually fixed it by adding a small line I'd have never thought to add. following the tutorial here

[http://iomem.com/index.php?archives/3-Starting-out-with-Lighttpd.html&serendipity](http://iomem.com/index.php?archives/3-Starting-out-with-Lighttpd.html&serendipity)[entrypage]=all

---

### Post by Nashdak on 2009-03-26
Hi,

would you please post here the "small line I'd have never thought to add" ?

Thanks.

---

### Post by commandant_gogo on 2010-06-23
guess it was 

> fastcgi.server = ( ".php" => ((
"bin-path" => "/usr/bin/php5-cgi",
"socket" => "/tmp/php.socket"
)))

---

### Post by ionplay on 2012-04-18
had the same problem on fresh lighttpd on ubuntu 10.04 install

triple checked permissions
and copying fastcgi.conf to enabled directory
etc....

ultimately the modules were not loaded (not sure how or why), but executed the following and it works properly now

sudo lighttpd-enable-mod fastcgi fastcgi-php

hope this helps anyone else landing on this page

---

### Post by oldos2er on 2012-04-18
Closed, necromancy.

---

