---
title: "Installing using wget"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by nel636 on 2008-12-17
Hi guys,

Im very new to linux so bare with me. im trying to install a copy of opsview on ubuntu 8.04 so i can monitor the netflow output on my cisco devices at work. i have opsview w/ LAMP setup and working OK. however im tring to download apps from the web. After a google i found you can use "wget (URL)" to retrieve apps from a website.

Ive tried installing webadmin and plugins for opsview and i get the following error:

```
http://sourceforge.net/project/downloading.php?group_id=58819
  (try:12) => `downloading.php?group_id=58819'
Connecting to sourceforge.net|216.34.181.60|:80... failed: Connection timed out.
Retrying.
```

The wget i am trying to run here is wget "http://dfn.dl.sourceforge.net/sourceforge/flavio/flavio-2.0.0.tar.gz"

This is to install a plugin for opsview. Ive also tried other url's and still no luck. ive tried this on another version of ubuntu (i have one in VM and one on a dell PC) and it does not work. im not sure if this is relating to the ubuntu box or what? the proxy is configured and works OK as i have downloaded dist-upgrades and opsview OK.

I can also ping the IP of the sourceforge server too so its not a routing issue.

Thanks

nel

---

### Post by Poyntz on 2008-12-17
i tried the same link... worked fine for me.

how fast is your connection? are you sure it's not timing out?
the proxy could be filtering out the download - if so it might be hard to do anything about i other than contact your provider.
have you tried other download methods and see if they worked. ie, have you tried firefox? is it installing on firefox?
is there a way to check if you've reached your internet download quota? that could be the issue...
a fix may be 
```
export HTTP_PROXY=http://proxyaddress:port; export HTTPS_PROXY=https://proxyaddress:port; export FTP_PROXY=ftp://proxyaddress:port
```
where proxyaddress is your proxy address and port is your port number

other than that try **System -> Preferences -> Network Proxy** and click **Apply System-Wide**

---

### Post by nel636 on 2008-12-17
Sorry i should have stated its installed on ubuntu server 8.04. SO there's no gui on the box. Yes i can definately ping the IP of the server.

Its at work so we have no cap and we have a fast internet connection and a squid proxy.

Could it be a firewall rule on the box blocking it?

Also would it be possible to download it via apt-get and place the URL in the sources.list file? ive tried entering:

```
deb http://dfn.dl.sourceforge.net/sourceforge/flavio/flavio-2.0.0.tar.gz
```

But when i try and run apt-get install XYZ it complains of the line i entered above so i assume i have the syntax or something on the line incorrect.

---

### Post by nel636 on 2008-12-17
Hi,

ive tried a ubuntu desktop 8.04 edition in a VM with my wget command and it works OK. so i would think its some kind of security issue to possibly prevent you installing things from the web on the server edition?

Anyone know? i would prefer to have this running on the server edition.

Thanks in advance

---

