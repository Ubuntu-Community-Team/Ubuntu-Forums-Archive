---
title: "Is Avira for Linux gone?"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by Cournot on 2009-10-27
I was trying to get the avira Antivirus from [www.free-av.de]("http://www.free-av.de"), where all references point, and I was unable to find any version for Linux. What am I missing? Is it suddenly gone? Thanks.

---

### Post by zvacet on 2009-10-28
Why do you want to install antivirus on Ubuntu?There is no need for that if you are average user.Read [this.]("http://ubuntuforums.org/showthread.php?t=510812&highlight=security")

---

### Post by kellemes on 2009-10-28
> **zvacet said:**
> Why do you want to install antivirus on Ubuntu?There is no need for that if you are average user.Read [this.]("http://ubuntuforums.org/showthread.php?t=510812&highlight=security")

Great link!

---

### Post by Cournot on 2009-10-28
> **zvacet said:**
> Why do you want to install antivirus on Ubuntu?There is no need for that if you are average user.Read [this.]("http://ubuntuforums.org/showthread.php?t=510812&highlight=security")

Well, I prefer to be on the safe side. Besides, I have to keep dual boot for professional reasons and want to be able to scan the Windows partition from Linux, Avira solves that. Or used to solve it, since it does seem to be gone for Linux.

---

### Post by howefield on 2009-10-28
> **Cournot said:**
> Avira solves that. Or used to solve it, since it does seem to be gone for Linux.

No, the links still lead you to a download for linux. You just need to look harder.

[http://www.free-av.de/en/download/download_servers.php](http://www.free-av.de/en/download/download_servers.php)

---

### Post by nickrout on 2009-10-28
> **zvacet said:**
> Why do you want to install antivirus on Ubuntu?There is no need for that if you are average user.Read [this.]("http://ubuntuforums.org/showthread.php?t=510812&highlight=security")

There are many reasons to install an antivirus program on linux.

On a mail server you can scan incoming mail for viruses

On a file server you can scan the files that your windows users are dumping on the lan.

You can analyse windows disks and machines.

etc etc.

---

### Post by Cournot on 2009-10-28
> **howefield said:**
> No, the links still lead you to a download for linux. You just need to look harder.

[http://www.free-av.de/en/download/download_servers.php](http://www.free-av.de/en/download/download_servers.php)


Many thanks. Seems you can't reach that so easily if you actually are in Germany, the download links lead to computer magazine download pages who have removed the Linux versions. Didn't occur to me to switch to English...

---

### Post by Wiebelhaus on 2009-10-28
The Best solution for Ubuntu Viral Safety , [Bit Defender for Unices]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html").

---

### Post by howefield on 2009-10-28
> **Cournot said:**
> Didn't occur to me to switch to English...

That's just the way I got there, but you don't have to switch to English, clicking on the sitemap link at the bottom of the homepage, then on the "Avira AntiVir Personal - FREE Antivirus" link takes you to a page with this link "Übersicht aller Sprachversionen inkl. Unix auf unseren Download Servern finden Sie hier" From there to the download page.

---

### Post by vinutux on 2009-10-28
Here | **[http://www.avira.com/en/products/avira_antivir_professional_3.html]("http://www.avira.com/en/products/avira_antivir_professional_3.html")**

---

### Post by Beezgetz on 2009-11-27
Oi,

I have just downloaded and installed AntiVir, this:
antivir-workstation-pers-3.0.5-12



which was successful, only I did not instal dazuko, althou I modified script as shovn here:
[http://ubuntuforums.org/showpost.php?p=8247061&postcount=4](http://ubuntuforums.org/showpost.php?p=8247061&postcount=4)

```
Would you like to install dazukofs now ? [y] y
installing dazuko ... Available Dazuko3-Package: '3.0.0-rc4'

checking for needed build components:
	checking for C compiler cc ... found
	checking for C compiler gcc ... found
	checking for kernel sources ... found
 
detecting kernel version ... 2.6.31
You try to install dazuko on a not supported kernel version.
Please visit [http://www.dazuko.org](http://www.dazuko.org) for more informations
Dazuko installation failed


```

As I was installing, it asked me if I wanted to have a panel icon for Guard, showing status. I have chosen y(es).

```
Would you like to install the AVIRA Guard GNOME plugin ? [n] y
installing AVIRA Guard GNOME plugin ... 
*** Installing pre-compiled applet
done
```


As I finished installation I ran update:
Update finished successfully


This was all in shell, root (elevated user).

Now, that icon is nowhere to be seen, and I also can not find AntiVir in my Application menu...


I ran some command lines:

```
root@compaq6820s:/home/grom/AntiVirus/antivir-workstation-pers-3.0.5-12# avscan status
Error: Failed to connect to Guard daemon
You need to start avguard before using on-demand scans.
You need root-access to do that.

root@compaq6820s:/home/grom/AntiVirus/antivir-workstation-pers-3.0.5-12# avscan start
Error: Failed to connect to Guard daemon
You need to start avguard before using on-demand scans.
You need root-access to do that.

root@compaq6820s:/home/grom/AntiVirus/antivir-workstation-pers-3.0.5-12# avguard status
Status: avguard.bin not running 
root@compaq6820s:/home/grom/AntiVirus/antivir-workstation-pers-3.0.5-12# avguard start
Starting AVIRA AntiVir Workstation Personal ...
Starting: avguard.bin
Warning: No dazuko module available, on-access protection disabled.
root@compaq6820s:/home/grom/AntiVirus/antivir-workstation-pers-3.0.5-12# avscan status
Avira AntiVir
Copyright (C) 2009 by Avira GmbH.
All rights reserved.
SAVAPI-Version: 3.0.5.19, AVE-Version: 8.2.1.78
VDF-Version: 7.10.1.117 created 20091127

AntiVir license: 0000149996

Info: automatically excluding /sys/ from scan (special fs)
Info: automatically excluding /proc/ from scan (special fs)
Info: automatically excluding /home/quarantine/ from scan (quarantine)

------ scan results ------
   directories: 0
 scanned files: 0
        alerts: 0
    suspicious: 0
     scan time: 00:00:01
--------------------------
root@compaq6820s:/home/grom/AntiVirus/antivir-workstation-pers-3.0.5-12# 

```



Still no icon... still no shortcut in Application menu...

Is this shell application, or should be there gui?

Help is appreciated!

Oh, and yes, I even restarted computer... and I am still a beginner in linux...

---

### Post by wilee-nilee on 2009-11-27
You can install clamtk and scan Linux and a dual boot MS.

---

### Post by Beezgetz on 2009-11-27
Hello

Synaptic says:
ClamTk is a GUI front-end for ClamAV using perl-Gtk2

i don't know how can this help me? Isn't ClamAV another anti-virus progtam?

And what is dual boot MS has to do with my problem? It seems that I do not understand.

Kind regards, Beezgetz

---

### Post by wilee-nilee on 2009-11-27
If you install clamtk it loads the whole clam set up and downloads the latest definitions. I don't really use it but I installed it from the terminal just out of curiosity. It is actually a good way of cleaning a MS system that isn't bootable because of infections so that you can get back in and use some of the better free, free standing AV programs like.
[http://www.malwarebytes.org/](http://www.malwarebytes.org/)
[http://www.superantispyware.com/download.html](http://www.superantispyware.com/download.html)
These to can be loaded to a open disc or thumb to get right at the problems if your being redirected by a infection.
I always suggest a fresh install in cases of a severe situation but many people store everything on their computers so a fresh install is not always a option. personally I just use my computers as OS and store the important stuff on a external HD.

---

### Post by Beezgetz on 2009-11-28
Oi Wilee,

I am not a native English speaker, but if I understand you correctly,
You are proposing I use other anti-virus program?

In that case, I have already made up my mind, amd I am using AntiVir anti-virus program. That is to say, if I can get gui for it.

So, if we stick to my problem, is there a gui for AntiVir?

...and what has MS (does that stand for microsoft?) has to do with anything?

As I said at the beginning, I am not good at english, and I might understood you wrong, in which case I will appreciate your extra effort!


My main question is still: Is there a GUI for AntiVir?

Kind regards, Beezgetz


Edit:

Hell no! I found this:
[http://forum.avira.com/wbb/index.php?page=Thread&postID=845516](http://forum.avira.com/wbb/index.php?page=Thread&postID=845516)

---

### Post by Soul-Sing on 2009-11-28
gui for antivir:
: [http://www.free-av.de/de/download/download_servers.php](http://www.free-av.de/de/download/download_servers.php)
```
cd ......
```
```
sudo ./install 
```
Press <ENTER> to view the license.
Do you agree to the license terms? [n] y
Enter the path to your key file: [hbedv.key]
Would you like to re-install the internet update daemon? [n]
How should AVGuard be installed? [k]
three possib.
default
[SIZE="3"]
module (m)[/SIZE]
default

[SIZE="3"]kernel (k)[/SIZE] 
default

[SIZE="3"]no install (n)[/SIZE]

Would you like AvGuard to start automatically? [y]

Would you like to install the GUI (+ SMC support)? [y]

Would you like to configure the AntiVir updater now? [y]

Would you like email notification about updates? [n]

Would you like the updater to log to a custom file? [y]

How often should AntiVir check for updates? [d]

(once a day (d))

Save configuration settings? [y]

Would you like to apply the new configuration? [y]

Would you like to start AvGuard now? [y]

[COLOR="Red"]gui?[/COLOR]
: ```
antivir-gui 
```

of not ===> /etc/avguard.conf
edit: "# Enable and configure GUI support" 
put/replace: 
# Enable and configure GUI support
GuiSupport  yes
GuiCAFile   /usr/lib/AntiVir/gui/cert/cacert.pem
GuiCertFile /usr/lib/AntiVir/gui/cert/server.pem
GuiCertPass antivir_default

source: german wiki

---

### Post by vvuk on 2010-02-13
Sorry for writing on closed theme but I just want to inform you that AV gui is available according to this site [http://wiki.ubuntuusers.de/AntiVir](http://wiki.ubuntuusers.de/AntiVir) which is dated on 28. Januar 2010. I will check that now...

---

### Post by lytithwyn on 2010-12-14
Here's a link to the download page for the free version as of 12/14/2010.  This page has links for both the windows version and the linux version.  I had a hard time getting to the right page, and I thought others might as well.

[http://www.avira.com/en/support-download-free-antivirus]("http://www.avira.com/en/support-download-free-antivirus")

---

