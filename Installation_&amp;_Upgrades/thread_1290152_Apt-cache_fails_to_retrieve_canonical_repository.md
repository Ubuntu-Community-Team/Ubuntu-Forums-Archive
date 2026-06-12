---
title: "Apt-cache fails to retrieve canonical repository"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by cirobr on 2009-10-13
Hello,

I have installed apt-cache on a server (IP 192.168.0.100) for deployment of updates to the client computers on the network.

Problem is: every time I run Synaptic on a client machine (for instance, IP 192.168.0.110) to reload packages, I get the following error on canonical repository. Synaptic network is configured for server's port 9999.

> [http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages)  404 file not found on backend

Config file follows. Thanks for providing any help on this.

```
[DEFAULT]
;; All times are in seconds, but you can add a suffix
;; for minutes(m), hours(h) or days(d)

;; Server IP to listen on
;address = 192.168.0.254

;; Server port to listen on
port = 9999

;; Control files (Packages/Sources/Contents) refresh rate
;;
;; Minimum age of a file before it is refreshed
min_refresh_delay = 1h

;; Minimum age of a file before attempting an update (NOT YET IMPLEMENTED)
;min_age = 23h

;; Uncomment to make apt-proxy continue downloading even if all
;; clients disconnect.  This is probably not a good idea on a
;; dial up line.
;; complete_clientless_downloads = 1

;; Debugging settings.
;; for all debug information use this:
;; debug = all:9
debug = all:4 db:0

;; Debugging remote python console
;; Do not enable in an untrusted environment
;telnet_port = 9998
;telnet_user = apt-proxy
;telnet_password = secret

;; Network timeout when retrieving from backend servers
timeout = 15

;; Cache directory for apt-proxy
cache_dir = /var/cache/apt-proxy

;; Use passive FTP? (default=on)
passive_ftp = on

;; Use HTTP proxy?
;http_proxy = [username:password@]host:port
;http_proxy = localhost:3128

;; Limit download rate from backend servers (http and rsync only), in bytes/sec
;bandwidth_limit = 100000

;;--------------------------------------------------------------
;; Cache housekeeping

;; Time to perform periodic housekeeping:
;;  - delete files that have not been accessed in max_age
;;  - scan cache directories and update internal tables
cleanup_freq = 1d

;; Maximum age of files before deletion from the cache (seconds)
max_age = 120d

;; Maximum number of versions of a .deb to keep per distribution
max_versions = 3

;; Add HTTP backends dynamicaly if not already defined? (default=on)
;dynamic_backends = on

;;---------------------------------------------------------------
;;---------------------------------------------------------------
;; Backend servers
;;
;; Place each server in its own [section]

[debian]
;; The main Debian archive
;; You can override the default timeout like this:
;timeout = 30

;; Backend servers, in order of preference
backends = 
	http://ftp.us.debian.org/debian
	http://ftp.de.debian.org/debian
	http://ftp2.de.debian.org/debian
	ftp://ftp.uk.debian.org/debian

min_refresh_delay = 1d

[security]
;; Debian security archive
backends = 
	http://security.debian.org/debian-security
	http://ftp2.de.debian.org/debian-security

min_refresh_delay = 1m

[ubuntu]
;; Ubuntu archive
;timeout = 60 ;wait 1 Minute
backends = http://br.archive.ubuntu.com/ubuntu
backends = http://archive.ubuntu.com/ubuntu
min_refresh_delay = 15m

[ubuntu-security]
;; Ubuntu security updates
timeout = 60 ;wait 1 Minute
backends = http://security.ubuntu.com/ubuntu
min_refresh_delay = 1m

[canonical]
;; Canonical archive
timeout = 60 ;wait 1 Minute
backends = http://archive.canonical.com/ubuntu
min_refresh_delay = 15m

[medibuntu]
;; Medibuntu archive
;timeout = 60 ;wait 1 Minute
;backends = http://packages.medibuntu.org
;backends = http://packages.medibuntu.org/dists
min_refresh_delay = 15m

;[backports.org]
;; backports.org
;backends = http://backports.org/debian
min_refresh_delay = 1d

;[blackdown]
;; Blackdown Java
;backends = http://ftp.gwdg.de/pub/languages/java/linux/debian
min_refresh_delay = 1d

;[debian-people]
;; people.debian.org
;backends = http://people.debian.org

;[emdebian]
;; The Emdebian project
;backends = http://emdebian.sourceforge.net/emdebian

;[rsync]
;; An example using an rsync server.  This is not recommended
;; unless http is not available, becuause rsync is only more
;; efficient for transferring uncompressed files and puts much
;; more overhead on the server.
;backends = rsync://ftp.uk.debian.org/debian
```

---

### Post by cirobr on 2009-10-22
No hint?

---

