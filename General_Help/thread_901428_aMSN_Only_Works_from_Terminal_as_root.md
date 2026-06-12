---
title: "aMSN Only Works from Terminal as root"
date: 2008-08-26
forum: General Help
---

### Post by Catsworth on 2008-08-26
If I try to launch aMSN from the graphical launcher in the menu it fails, with no error messages.

If I try to launch it from a normal terminal I get the following error:

```
Error in startup script: error flushing "sock8": connection refused
    while executing
"flush $sck"
    (procedure "::Socks5::Init" line 47)
    invoked from within
"::Socks5::Init $sock $proxy_serv $proxy_port $proxy_authenticate $proxy_user $proxy_password"
    (procedure "::ProxyDirect::Snit_methodconnect" line 40)
    invoked from within
"$proxy connect $name"
    (procedure "cmsn_socket" line 13)
    invoked from within
"cmsn_socket ns"
    (procedure "cmsn_ns_connect" line 35)
    invoked from within
"cmsn_ns_connect $username $passwd"
    (procedure "::MSN::connect" line 29)
    invoked from within
"::MSN::connect"
    invoked from within
"if { $argv != "" && [LoginList exists 0 $argv] } {
   after idle [list auto_login_argv $argv] 
} else {
   if { [::config::getKey autoconnect] == 1 &&..."
    (file "/usr/bin/amsn" line 365)
X Error of failed request:  RenderBadPicture (invalid Picture parameter)
  Major opcode of failed request:  156 (RENDER)
  Minor opcode of failed request:  7 (RenderFreePicture)
  Picture id in failed request: 0x340014b
  Serial number of failed request:  3911
  Current serial number in output stream:  4001
```

If I launch it from a terminal as root, or using gksudo, it runs fine.

I've tried with the version from the repo's and the latest version.

Anybody got any ideas what's going on?

Thanks :)

---

### Post by Sycron on 2008-08-26
Use pidgin 2.5.0 [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin) .

Make sure you unninstal the older version.
```
sudo apt-get remove pidgin pidgin-data libpurple0
```

Get all those three debs on your [COLOR="Red"]home/pidgin[/COLOR] folder, and type in a terminal ```
sudo dpkg -i ~/pidgin/*.deb
```
If you get a error then type
```
sudo apt-get install -f
```
And type again ```
sudo dpkg -i ~/pidgin/*.deb
```
Also you may see the changelog [http://developer.pidgin.im/wiki/ChangeLog](http://developer.pidgin.im/wiki/ChangeLog) .

Hope it helps.

---

### Post by gjoellee on 2008-08-26
is it the last version of aMSN? MSN Messenger changed server or something for not a so long time ago and to log on to the MSN network you will need the last version...
```
sudo apt-get remove amsn && sudo apt-get install amsn
```

---

### Post by jerome1232 on 2008-08-26
might want to make that 
```
sudo apt-get remove --purge amsn
sudo apt-get clean
sudo apt-get update
sudo apt-get install amsn
```

---

### Post by gjoellee on 2008-08-26
> **jerome1232 said:**
> might want to make that 
```
sudo apt-get remove --purge amsn
sudo apt-get clean
sudo apt-get update
sudo apt-get install amsn
```
:popcorn:

---

### Post by Catsworth on 2008-08-28
Nope, still crashes unless I open it with root priv's.

Any other ideas?

---

### Post by ad_267 on 2008-08-28
Don't know about fixing aMSN but emesene is a pretty good alternative for MSN too and it's a gtk app.

---

### Post by Catsworth on 2008-09-02
Anybody else got any thoughts on this?

---

### Post by AlanR8 on 2008-09-02
Nothing constructive I'm afraid. I had this issue as well, started about 3 weeks ago and I can't get AMSN to connect at all. I just tried running it from the CL as Root and the connection's still refused.

I switched to Pidgin and it works fine. Not the answer you're looking for but at least it's a solution

---

### Post by chadeldridge on 2008-09-02
Have you tried installing the newer AMSN version from their site and not the one from repo ... last install of it I had was months out of date from the repo.  But in the end Pidgin is far superior unless you need webcam support.

---

### Post by DarkFull on 2008-09-03
> **Catsworth said:**
> If I try to launch aMSN from the graphical launcher in the menu it fails, with no error messages.

If I try to launch it from a normal terminal I get the following error:

```
Error in startup script: error flushing "sock8": connection refused
    while executing
"flush $sck"
    (procedure "::Socks5::Init" line 47)
    invoked from within
"::Socks5::Init $sock $proxy_serv $proxy_port $proxy_authenticate $proxy_user $proxy_password"
    (procedure "::ProxyDirect::Snit_methodconnect" line 40)
    invoked from within
"$proxy connect $name"
    (procedure "cmsn_socket" line 13)
    invoked from within
"cmsn_socket ns"
    (procedure "cmsn_ns_connect" line 35)
    invoked from within
"cmsn_ns_connect $username $passwd"
    (procedure "::MSN::connect" line 29)
    invoked from within
"::MSN::connect"
    invoked from within
"if { $argv != "" && [LoginList exists 0 $argv] } {
   after idle [list auto_login_argv $argv] 
} else {
   if { [::config::getKey autoconnect] == 1 &&..."
    (file "/usr/bin/amsn" line 365)
X Error of failed request:  RenderBadPicture (invalid Picture parameter)
  Major opcode of failed request:  156 (RENDER)
  Minor opcode of failed request:  7 (RenderFreePicture)
  Picture id in failed request: 0x340014b
  Serial number of failed request:  3911
  Current serial number in output stream:  4001
```

If I launch it from a terminal as root, or using gksudo, it runs fine.

I've tried with the version from the repo's and the latest version.

Anybody got any ideas what's going on?

Thanks :)


[RESOLVIDO]

sudo kedit wish8: /usr/bin/amsn
--------------------------------------------------------------------/
if { $argv != "" } {
   after idle [list auto_login_argv $argv] 
} else {
   if { [::config::getKey autoconnect] == 1 && [::config::getKey save_password] == 0} {
     	::MSN::connect
   }
}
---------------------------------------------------------------------/
Trocar "save_passwod] == 1}"   POR "save_passwod] == 0}"

---

### Post by DarkFull on 2008-09-03
[RESOLVIDO]

sudo kedit wish8: /usr/bin/amsn
--------------------------------------------------------------------/
if { $argv != "" } {
after idle[list auto_login_argv $argv]
} else {
if { [::config::getKey autoconnect] == 1 && [::config::getKey save_password] == 0} {
::MSN::connect
}
}
---------------------------------------------------------------------/
Trocar "save_passwod] == 1}" POR "save_passwod] == 0}"

---

