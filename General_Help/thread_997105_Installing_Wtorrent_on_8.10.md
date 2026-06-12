---
title: "Installing Wtorrent on 8.10"
date: 2008-11-29
forum: General Help
---

### Post by SoulSmasher on 2008-11-29
Hi, i couldn't find a guide for installing wtorrent to ubuntu 8.10 32 bits
i installed rtorrent from synaptic

is there any guide to install & use it

Any help would be kindly appreciated
Thanks

---

### Post by oldos2er on 2008-11-29
[http://filesharefreak.com/tutorials/how-to-svn-rtorrent-wtorrent-rtorrent-webui/](http://filesharefreak.com/tutorials/how-to-svn-rtorrent-wtorrent-rtorrent-webui/)

---

### Post by Ledger on 2008-11-29
> **oldos2er said:**
> [http://filesharefreak.com/tutorials/how-to-svn-rtorrent-wtorrent-rtorrent-webui/](http://filesharefreak.com/tutorials/how-to-svn-rtorrent-wtorrent-rtorrent-webui/)
That tutorial is for Debian.

---

### Post by oldos2er on 2008-11-29
> **Ledger said:**
> That tutorial is for Debian.

 Since Ubuntu is based on Debian, I don't see why it wouldn't work. I haven't used it, but reading through it nothing obviously "wrong" catches my eye.

---

### Post by SoulSmasher on 2008-11-30
well, i tired following both wtorrent's and the guide given above, i'm using lighttpd and i still get this
[IMG]http://img372.imageshack.us/img372/8544/semttuloos5.jpg[/IMG]

this is the guide i followed when the guide given above didn't work:
[http://www.wtorrent-project.org/trac/wiki/wTorrentInstall](http://www.wtorrent-project.org/trac/wiki/wTorrentInstall)

this is my lighttpd.conf:
```
# Debian lighttpd configuration file
#

############ Options you really have to take care of ####################

## modules to load
# mod_access, mod_accesslog and mod_alias are loaded by default
# all other module should only be loaded if neccesary
# - saves some time
# - saves memory

server.modules              = (
"mod_scgi",
"mod_auth",

            "mod_access",
            "mod_alias",
            "mod_accesslog",
            "mod_compress",
#           "mod_rewrite",
#           "mod_redirect",
#           "mod_evhost",
#           "mod_usertrack",
#           "mod_rrdtool",
#           "mod_webdav",
#           "mod_expire",
#           "mod_flv_streaming",
#           "mod_evasive"
)

## a static document-root, for virtual-hosting take look at the
## server.virtual-* options
server.document-root       = "/var/www/"

## where to upload files to, purged daily.
server.upload-dirs = ( "/var/cache/lighttpd/uploads" )

## where to send error-messages to
server.errorlog            = "/var/log/lighttpd/error.log"

## files to check for if .../ is requested
index-file.names           = ( "index.php", "index.html",
                               "index.htm", "default.htm",
                               "index.lighttpd.html" )


## Use the "Content-Type" extended attribute to obtain mime type if possible
# mimetype.use-xattr = "enable"

#### accesslog module
accesslog.filename         = "/var/log/lighttpd/access.log"

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

## Use ipv6 only if available.
include_shell "/usr/share/lighttpd/use-ipv6.pl"

## bind to port (default: 80)
server.port  = 81 # RT_PORT


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
#server.errorfile-prefix    = "/var/www/"

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
## read /etc/lighttpd/conf-available/README first
include_shell "/usr/share/lighttpd/include-conf-enabled.pl"

#### handle Debian Policy Manual, Section 11.5. urls
## by default allow them only from localhost
## (This must come last due to #445459)
## Note: =~ "127.0.0.1" works with ipv6 enabled, whereas == "127.0.0.1" doesn't
$HTTP["remoteip"] =~ "127.0.0.1" {
	alias.url += (
		"/doc/" => "/usr/share/doc/",
		"/images/" => "/usr/share/images/"
	)
	$HTTP["url"] =~ "^/doc/|^/images/" {
		dir-listing.activate = "enable"
	}
}

scgi.server = (
 "/RPC2" => # RT_DIR
  ( "127.0.0.1" =>
   (
    "host" => "127.0.0.1", # Ip where rtorrent is listening
    "port" => 5000, # Port specified in .rtorrent.rc
    "check-local" => "disable"
   )
  )
 )

auth.backend = "htdigest"
auth.backend.htdigest.userfile = "/var/www/.wtorrent_users"
auth.require = ( "/RPC2" =>
 (
  "method" => "basic",
  "realm" => "XML-RPC",
  "require" => "valid-user"
 )
)



#url.access-deny = ("~", ".inc", ".db", ".tpl.php", ".cls.php",)

```

there's a RPC2 at / folder which is 777 chmodded
this is my .wtorent_users file at var/www (autogenerated with a file given at guide)
```
wtorrent:XML-RPC:313eca40c30ba43e64b1400b7c57b71f
```
this is my .rtorrent.rc file at my home folder
```
scgi_port = localhost:5000
```

and this is my wtorrent configuration file:
```
<?php
/* wTorrent autoconfiguration file. Created 30/11/2008 */
define ('LANGUAGE', 'en');
define ('DB_FILE', 'db/database.db');
define ('RT_HOST', 'localhost');
define ('RT_PORT', 81);
define ('RT_DIR', '/RPC2');
define ('RT_AUTH', true);
define ('RT_USER', 'myusername'); //refering to my .wtorrent_users file
define ('RT_PASSWD', 'mypass'); //refering to my .wtorrent_users file
define ('NO_MULTICALL', true);
define ('EFFECTS', true);
define ('DIR_TORRENTS', 'torrents/');
define ('DIR_EXEC', '/var/www/');
define ('DIR_DOWNLOAD', 'data/');
?>
```

what's missing? i made it run once, but after restart now it doesn't :(

thanks

edit: i removed libtorrent & rtorrent and installed from SVN as guide describes

---

### Post by SoulSmasher on 2008-11-30
*bump* any ideas ?

---

### Post by Jonsson84 on 2008-12-01
Has anyone got this working for them in 8.10? 
I also would like a guide on how to get this up and running, tried both the guides above but always end up with the "Error: Could not connect to rtorrent"

/Jonsson

---

### Post by SoulSmasher on 2008-12-03
guess no one knows :-/

---

### Post by Vasto on 2008-12-07
Did you ever figure it out? I'm having trouble too.

Also, are you running rTorrent as root? For some reason I have to but I would rather not.

---

### Post by oiad on 2008-12-16
This guide works for 8.10.  Make sure you have all of your file permissions right, it slowed me down a little.  Just ignore the first section on using a VE (unless that is what you want).

[http://robert.penz.name/82/howto-install-rtorrent-and-wtorrent-within-an-ubuntu-hardy-ve/](http://robert.penz.name/82/howto-install-rtorrent-and-wtorrent-within-an-ubuntu-hardy-ve/)

---

### Post by No-Neck on 2008-12-16
You cannot install rtorrent from a package, it needs to be compiled with xmlrpc-c support. Here is a guide, it was written for Debian but has a package list for Ubuntu (the rest is nigh on identical). It is written and tested by me on Debian Etch, Ubuntu Hardy and Intrepid. Let me know how you get on.

---

### Post by oiad on 2008-12-16
I followed the guide that I posted previously and I now noticed that mine won't display the torrents in wtorrent, but everything else works right.  I can add torrents, control bandwidth, etc but on the wtorrent main page it just says "No Torrents Found".  The torrents are added fine from wtorrent and start up in rtorrent.  On the main page where it states the current up/down usage it is accurate even though there is no files listed?  Any ideas?

---

### Post by No-Neck on 2008-12-17
What the hell, I forgot to paste the link. o.O

[http://www.wtorrent-project.org/trac/wiki/DebianInstall](http://www.wtorrent-project.org/trac/wiki/DebianInstall)

oiad, it's hard to say. Before I compiled the above guide I had followed a few different ones, each ended with different problems, I found the easiest way was to start from scratch rather than troubleshooting something I didn't fully understand.

---

### Post by Equiquay on 2009-01-05
It took me a while, but I finally got rtorrent/wtorrent working on 8.10 server with the help of the guides listed previously on this thread.

Here are some tips:

1.  You don't need to install xmlrpc-c, or compile rtorrent with xmlrpc-c support.  It's already built in.  Just:

```
sudo apt-get install rtorrent
```

2.  If you're using lighttpd for your webserver, add 

```
"mod_scgi"
```

to the server.modules section of /etc/lighttpd/lighttpd.conf, and also add the following somewhere in the file:

```
scgi.server = (
"/RPC2" => # RT_DIR
( "127.0.0.1" =>
(
"host" => "127.0.0.1", # Ip where rtorrent is listening
"port" => 5000, # Port specified in .rtorrent.rc
"check-local" => "disable"
)
)
)
```

This way, you don't have to make any symlinks to /etc/lighttpd/conf-enabled/.  (Note: This doesn't give you any authentication.  If you want it, read the article at [http://www.wtorrent-project.org/trac/wiki/DebianInstall](http://www.wtorrent-project.org/trac/wiki/DebianInstall))

3.  Again, for lighttpd, use this command to enable fastcgi:

```
sudo lighty-enable-mod fastcgi
```


Many thanks to the people who wrote the guides above!

---

### Post by Tiny Grasshopper on 2009-02-24
[http://tinygrasshopper.blogspot.com/2008/09/how-to-install-and-setup-web-based.html](http://tinygrasshopper.blogspot.com/2008/09/how-to-install-and-setup-web-based.html)

disclaimer: it's my blog post. please handle with care

---

### Post by devinw on 2009-03-12
If anyone's interested, I've written an installation script that automates the process of installing wTorrent/rTorrent on Ubuntu: [http://ubuntuforums.org/showthread.php?t=1064377](http://ubuntuforums.org/showthread.php?t=1064377)

---

