---
title: "Add KDE To 8.04 LTS Text-Only?"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by smpoole7 on 2009-09-19
This may sound like a strange question, but I'm new to Ubuntu. (Totally new.) I installed the 8.04 LTS Server for use as a server, then realized that setting it up would be a lot easier with graphical config tools. I decided to add KDE (since I prefer it to Gnome) with

sudo apt-get install kde

... and it churned and chugged for quite some time, then declared it installed and happy. OK ... (gulp, blush) ... so how do I start it? :)

startx doesn't work. Obviously, it needs to be configured first, but how do I do that? I've done a dozen Google searches, and I've searched here in the forum, but every single result always *assumes* that you've already got the Gnome desktop running and just want to *add* KDE to that. All of the suggestions say something like, "Click on System, then click This, then click That ..."

Ummm. I have nowhere to click. There's very little info (that I could find, anyway), about converting a text-only LTS installation to graphical.

I'm perfectly comfortable at a text prompt. If you can suggest the magical, mystical series of commands to be entered to make this happen, I'll be a happy man. :)

Thanks in advance!

Edited: In case it's not clear, I installed the server as text-only -- in fact, I downloaded the single-CD installer and used that. My server is currently the equivalent of what we'd call "text only/initdefault 3" over in the Suse/Red Hat/CentOS/etc. land in which I've lived for years ...

---

### Post by SuperSonic4 on 2009-09-19
What does the following do?

```
sudo /etc/init.d/kdm start
```


A reboot usually works wonders but I don't know if it's an option for you

If these don't work (or are not applicable) canyou post the output of ```
cat ~/.xinitrc
```

---

### Post by smpoole7 on 2009-09-19
> **SuperSonic4 said:**
> What does the following do?

```
sudo /etc/init.d/kdm start
```A reboot usually works wonders but I don't know if it's an option for you

If these don't work (or are not applicable) canyou post the output of ```
cat ~/.xinitrc
```

Thanks for the quick reply, and we're already getting somewhere. There IS no "kdm" in init.d, so it CAN'T start. (The result of the first command, of course, was "command not found.") Nor is there an ".xinitrc" file in my /home/stephen directory. Interesting.

Remember, all I did was "sudo apt-get install kde." Doubtless there are other steps I need to take, I just don't know what to do. If this was Suse, I'd run "sax -r" to get things configured. Edited: I forgot to mention: yes, I DID reboot after the installation.

---

### Post by smpoole7 on 2009-09-19
OK, KDE was installed, but that's it. It only installed KDE and its libraries; KDM wasn't installed, .xinit wasn't set up properly, etc., etc.  I'm now trying

```

sudo apt-get install kubuntu-desktop

```

... and it's downloading another 270MB of packages. (The first download was over 300MB!). Let's see if that works.

---

### Post by SuperSonic4 on 2009-09-19
Installing kdm would have been easier but it ought to work with that package installed

---

### Post by smpoole7 on 2009-09-19
> **SuperSonic4 said:**
> Installing kdm would have been easier but it ought to work with that package installed

It does indeed! After rebooting, it came up in the Kubuntu desktop.

I decided just to install the Kubuntu package to ensure that I had all the Ubuntu-related config stuff. Once-burned, twice shy and all that. :)

Thanks for the help. Of course, now for the REAL test. I did this in a VirtualBox here at home just to get a feel for what to do. NOW I get to install the same thing and get it running, plus VNC, on the server 50 miles away via SSH! :)

(And THEN I'll install the new mail server in the box!)

---

### Post by SuperSonic4 on 2009-09-19
> **smpoole7 said:**
> It does indeed! After rebooting, it came up in the Kubuntu desktop.

I decided just to install the Kubuntu package to ensure that I had all the Ubuntu-related config stuff. Once-burned, twice shy and all that. :)

Thanks for the help. Of course, now for the REAL test. I did this in a VirtualBox here at home just to get a feel for what to do. NOW I get to install the same thing and get it running, plus VNC, on the server 50 miles away via SSH! :)

(And THEN I'll install the new mail server in the box!)

Whatever works for you. I think there is a metapackage called kde-core which will install the core kde stuff including kdm but do not quote me on it.

Also good luck!

---

