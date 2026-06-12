---
title: "Small Java problem"
date: 2008-09-03
forum: General Help
---

### Post by Thrasonic on 2008-09-03
Hi all.  My Ubuntu is running very well, but I need to be able to use Webex from within Firefox in Ubuntu and it gets hung up due to some strange Java issue (strange to me, anyway).

Here's what the terminal reports:

jon@H04281971U8041:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)
jon@H04281971U8041:~$ 
jon@H04281971U8041:~$ 

To me it looks like all is well, but when I go to test my Java the test fails (it just continues to loop, it doesn't actually say it failed) and I get the little pop-up that says "Install Missing Plugins" and "Additional plugins are required..."  The Webex join meeting test page is here - [http://developers.webex.com/api/jointest/index.php](http://developers.webex.com/api/jointest/index.php) - and this one  gives me the same pop-up that going straight to the Java test page gives me.

Any ideas on what I can do?

---

### Post by Diabolis on 2008-09-03
The Java plug-in is a different thing from the the Java Runtime Environment (JRE). So, all what you need is to install the plug-in.
```
sudo apt-get install sun-java6-plugin
```

---

### Post by Thrasonic on 2008-09-03
> **Diabolis said:**
> The Java plug-in is a different thing from the the Java Runtime Environment (JRE). So, all what you need is to install the plug-in.
```
sudo apt-get install sun-java6-plugin
```

Hi Diabolis.  Thanks for the reply.  Here's what I got when I ran  that command:

jon@H04281971U8041:~$ sudo apt-get install sun-java6-plugin
[sudo] password for jon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jon@H04281971U8041:~$ 

Any ideas?

---

### Post by Denestria on 2008-09-04
Firefox may need help finding the java plugin.  Create a symlink from the libjavaplugin_oji.so to the firefox plugin directory.
```

sudo ln -s /usr/lib/java/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so
```
Your directories may not be exactly the same so change the command to the correct directories for your system.

---

### Post by Thrasonic on 2008-09-04
> **Denestria said:**
> Firefox may need help finding the java plugin.  Create a symlink from the libjavaplugin_oji.so to the firefox plugin directory.
```

sudo ln -s /usr/lib/java/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so
```
Your directories may not be exactly the same so change the command to the correct directories for your system.

Cool, I'll give this a try later on tonight.  Thanks.

---

### Post by Denestria on 2008-09-04
Actually, from another thread try
```

sudo update-java-alternatives -s java-6-sun

```
first to update links and then open Firefox and see if java shows up in the plugins.

---

### Post by Thrasonic on 2008-09-04
> **Denestria said:**
> Actually, from another thread try
```

sudo update-java-alternatives -s java-6-sun

```
first to update links and then open Firefox and see if java shows up in the plugins.

Okay, I ran this one, opened Firefox back up and tried the Webex site but it didn't work again.  How do I check to see if Java shows up in the plugins?

---

### Post by Denestria on 2008-09-04
In the Firefox address bar
```
about:plugins

```

---

### Post by Thrasonic on 2008-09-04
> **Denestria said:**
> In the Firefox address bar
```
about:plugins

```

Thanks.  Here's what it showed:

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

So from this I'm assuming Java still isn't working.  Should I do run the other line of code you suggested?

---

### Post by Denestria on 2008-09-04
Go ahead and give it a try.  If it doesn't work or you find a more elegant solution later all you have to do is remove the link you made.

---

### Post by Thrasonic on 2008-09-05
> **Denestria said:**
> Go ahead and give it a try.  If it doesn't work or you find a more elegant solution later all you have to do is remove the link you made.

Will do.  I'm at work now so I'll be trying this either later tonight or tomorrow.  I'll keep you posted.

---

### Post by jamesstansell on 2008-09-06
> **Thrasonic said:**
> Will do.  I'm at work now so I'll be trying this either later tonight or tomorrow.  I'll keep you posted.

You are running Ubuntu 8.04.1 right?  Do you have Firefox 3 or are you still running the old Firefox 2 version?

There were some issues with Firefox 2 and Java in the original 8.04 release.  I think (but I haven't verified) that they've been fixed for 8.10 but I'm not sure if they made it into 8.04.1.

Here's a web page that helps check your plugins without needing the about:plugins trick.

[http://gemal.dk/browserspy/plugins.html](http://gemal.dk/browserspy/plugins.html)

---

### Post by Bucky Ball on 2008-09-06
Java problematic. Were re-written and now available as:

openjdk-6-doc package

By Sun and improved by the sounds of other posters.

---

### Post by Thrasonic on 2008-09-07
> **jamesstansell said:**
> You are running Ubuntu 8.04.1 right?  Do you have Firefox 3 or are you still running the old Firefox 2 version?

There were some issues with Firefox 2 and Java in the original 8.04 release.  I think (but I haven't verified) that they've been fixed for 8.10 but I'm not sure if they made it into 8.04.1.

Here's a web page that helps check your plugins without needing the about:plugins trick.

[http://gemal.dk/browserspy/plugins.html](http://gemal.dk/browserspy/plugins.html)

Hi James.  I'm using 8.4.01 like you said and Firefox 2, not 3.  I'm using 2 because my school doesn't support 3 yet.  I'll check out the link before doing anything else.  Thanks.

---

### Post by Thrasonic on 2008-09-07
> **Bucky Ball said:**
> Java problematic. Were re-written and now available as:

openjdk-6-doc package

By Sun and improved by the sounds of other posters.

Hi Bucky Ball.  So do you recommend I remove whatever Java I have at this time and install the openjkd-6 version or package?

---

### Post by Bucky Ball on 2008-09-07
I'll update that. I did a bit more investigation and was starting to have some odd problems myself. Last night I went into Synaptics and removed ubuntu-restricted-extras then reinstalled and everything seems to be working sweet. It seems that this reinstalled both openjdk-6-doc package and sun-java-jre.

\\:D/

Give that a go.

---

