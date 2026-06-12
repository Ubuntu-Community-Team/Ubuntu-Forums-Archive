---
title: "APC PowerChute Network Shutdown"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by khalphen on 2009-07-28
Okay, so I have been battling this for a while.
I just recently got apcupsd to install properly along with java, so that's a push in the right direction, but I am still having a problem with pcns233. Here is a link to what my problem looks like:
 
[http://pastebin.ca/1510634](http://pastebin.ca/1510634) :(
 
If anyone knows how I can get it to set up the installation properly so that it's running and it sees itself, please let me know what I need to do, because I'm truly beating my head against the wall!

---

### Post by tgalati4 on 2009-07-28
Configuring startup files ...
Startup script=/etc/rc.d/init.d/PowerChute
cp: cannot create regular file `/etc/rc.d/init.d/PowerChute': 

A quick look:

Control scripts are (or should be) contained in /etc/init.d not /etc/rc.d/init.d
Try copying the PowerChute control script to /etc/init.d and rerun the package configurator.

What does PowerChute do that the other control panels don't?

tgalati4@tpad-Gloria7 ~/Desktop $ apt-cache search apcupsd
apcupsd - APC UPS Power Management (daemon)
apcupsd-cgi - APC UPS Power Management (web interface)
apcupsd-doc - APC UPS Power Management (documentation/examples)
gapcmon - apcupsd monitor GUI
gkrellmapcupsd - gkrellm plugin displaying the current processor speed

I've had apcupsd running for the past 3 years and it has shut down network computers listening for it about 3 or 4 times with power outages.
I don't use powerchute, although I remember the windows version--it was pretty-looking, but the bottom line is the linux barebones tools work.

---

### Post by barret1 on 2011-04-06
Sorry to reply to an old thread. As suggested by tgalati4, the issue is that it is using the wrong locations for the startup scripts. To get PowerChute Network Shutdown working, edit install.sh

Under the section which begins (ctrl-w in nano)
```
Initialize() {
    Echo "Initializing ..."
    case "$OS" in
```
Change the section which begins $LINUX to read
```
    $LINUX)
            STARTUP=/etc/init.d/PowerChute
        PCBE_STARTUP=/etc/rc.d/init.d/PBEAgent
        PCS_STARTUP=/etc/rc.d/init.d/pcs
        ;;
```
Finally, when the install is done, ignore the error messages, and execute the following as root
```
ln -s /etc/init.d/PowerChute /etc/rc0.d/K99PowerChute
ln -s /etc/init.d/PowerChute /etc/rc1.d/K99PowerChute
ln -s /etc/init.d/PowerChute /etc/rc2.d/S99PowerChute
ln -s /etc/init.d/PowerChute /etc/rc3.d/S99PowerChute
ln -s /etc/init.d/PowerChute /etc/rc4.d/S99PowerChute
ln -s /etc/init.d/PowerChute /etc/rc5.d/S99PowerChute
ln -s /etc/init.d/PowerChute /etc/rc6.d/K99PowerChute
```

And then run
```
sudo /etc/init.d/PowerChute start
```

Hopefully this will help someone!

---

### Post by Nathan Friend on 2012-03-12
Also you need to add a directory before starting pcns.

```
mkdir /var/lock/subsys/
```

---

