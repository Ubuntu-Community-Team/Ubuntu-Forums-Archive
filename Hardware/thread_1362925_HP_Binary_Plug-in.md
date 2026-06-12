---
title: "HP Binary Plug-in"
date: 2009-12-23
forum: Hardware
---

### Post by Glendon on 2009-12-23
After upgrading to 9.10 I wasn't able to print or scan with my HP Laserjet m1319f MFP.

So I thought I would just re-install it with hplip. 

The problem is that when I try to install the required binary plug-in, I get an error message:

ERROR: Plug-in file does not match its digital signature.
File may have been corrupted or altered.
Error code: 2

Has anyone experienced this before?

---

### Post by Manyette on 2009-12-23
Are you aware that you must uninstall the prveuius hplip installation before adding the new one?  It must be removed before a re-install.  To do so,m see this page:

[http://hplipopensource.com/node/188](http://hplipopensource.com/node/188)

I hope this is the answer for you, if you haven't tried this.

---

### Post by Glendon on 2009-12-24
I just did a remove using Synaptic. 

I'll follow the steps in the link and report back.

Thank you for your help.

---

### Post by Glendon on 2009-12-24
As I was replying I was installing 3.9.12 of hplip that I had downloaded. 

I looked at the website you linked to and figured I would follow those uninstallation instructions after the install finished. 

Well, the install finished and appeared to download a good binary plug-in. 

However, the installation of the plugin failed and reported a diff't error. 

I'm going to do the uninstall and reinstall thing now. 

Thanks.

---

### Post by Glendon on 2009-12-24
Followed the instructions to uninstall and then reinstalled.

I'm now printing.

Thanks!

---

### Post by Manyette on 2009-12-24
Hi Glendon, Believe me, I also learned it the hard way.  Glad it's working for you.

---

### Post by ndemou on 2010-05-17
I'll just put a note for 10.04 here to help others:

I have an HP-1120n (network printer). I did a clean 10.04 installation and then the installation of the printer went really fine with no error message or anything abnormal. The printer was added and everything was looking good except I couldn't print :).

Opening HPLIP I noticed that it was having a cryptic option to "install required plugin" (no other details anywhere about what the plugin was for". Clicking on this option started a wizard that eventually quit with an error "Installation of the plugin failed".

To fix it I had to:
1) open hplip (from the tray) 
2) uninstall the printer
3) run hp-setup as root to install the printer again (from a terminal run sudo hp-setup )

---

### Post by oroles on 2011-09-17
> **Manyette said:**
> Are you aware that you must uninstall the prveuius hplip installation before adding the new one?  It must be removed before a re-install.  To do so,m see this page:

[http://hplipopensource.com/node/188](http://hplipopensource.com/node/188)

I hope this is the answer for you, if you haven't tried this.

I have the same problem. I've tried in vane all hplip version.
How can i resolve the problem. I can't print anything...

---

### Post by pstickar on 2011-09-24
> **oroles said:**
> I have the same problem. I've tried in vane all hplip version.
How can i resolve the problem. I can't print anything...


Hi,

you may want to check:

[https://answers.launchpad.net/hplip/+question/171380](https://answers.launchpad.net/hplip/+question/171380)

It did not work smoothly for me, though:

[https://answers.launchpad.net/hplip/+question/172179](https://answers.launchpad.net/hplip/+question/172179)

Good luck,
p.

---

### Post by Raybo on 2011-10-31
It was ugly but I finally got my HP MFP to work.  I think the hp-setup bombs because the openprinting.org site is down.  I was able to download the plugin file from hp at:
[http://hplipopensource.com/hplip-web/plugin/](http://hplipopensource.com/hplip-web/plugin/)[COLOR="DarkRed"]hplip-3.11.10-plugin.tar[/COLOR]

Where in dark red substitute your version numbers.  Extract the tar file and then in hp-setup browse to that .run file.

---

