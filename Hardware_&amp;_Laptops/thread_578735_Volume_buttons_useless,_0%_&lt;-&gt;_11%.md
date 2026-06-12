---
title: "Volume buttons useless, 0% &lt;-&gt; 11%"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by Zorael on 2007-10-17
Pressing the volume-down button lowers it to 0%, and pressing the volume-up one raises it to 11%. It can't go higher than that, and there's no noticable volume change on any channel. It worked fine in Feisty.

The system is an Acer laptop, and I'm running **Kubuntu** Gutsy RC. (It's due release in mere hours, so no point putting this in the soon-to-be-closed forum.)

```
zorael@azrael:/etc/X11$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```


Sound works great if I use KMix to raise and lower volume, so I'm not really sure what pressing the keys actually does.

Is there some easy way to change which channel they control? And again, I'm running Kubuntu, so Gnome solutions wouldn't help much. :)

---

### Post by Zorael on 2007-10-18
This is without any extra fluff like Compiz-Fusion, I might add. Also, bump.

---

### Post by fadain on 2007-10-18
I can confirm this bug and I am running kubuntu on acer laptop too.

---

### Post by wastedfluid on 2007-10-18
I can confirm this, as well..

with An Acer 5100.


I'll bump, and save.. so I can check later.

---

### Post by Zorael on 2007-10-25
To clarify, **the buttons themselves DO work**, but they don't raise or lower the volume. (of any useful sound channel)

For instance, it could be trying to raise and lower a binary channel, one that could either be on or off. Or muting and unmuting a channel. I've no idea.

I'm going to try out these next links when I get home, but they seem to be aimed towards people whose laptops don't react to the keys being pressed, rather than the volume applet they call not functioning.

[https://wiki.ubuntu.com/KubuntuVolumeHotkeys?highlight=%28xmodmap%29](https://wiki.ubuntu.com/KubuntuVolumeHotkeys?highlight=%28xmodmap%29)
[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)
[https://wiki.kubuntu.org/KDEMultimediaKeys](https://wiki.kubuntu.org/KDEMultimediaKeys)

---

### Post by Jarn on 2007-10-26
It appears to be a known bug in kmilo that was reported three months ago with no love for it. :(

[https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/118723](https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/118723)

---

### Post by joao82 on 2007-10-28
I have the same problem too. It sucks now and it worked just fine on 7.04
re-re-bump, for the love of god.

---

### Post by randcoop on 2007-10-29
This is a bug that's getting no attention from the developers.  There are supposedly a few possible work-arounds, though I've tried none of them.

One is to install kmilo-legacy from the Gutsy repositories.  Some people claim that it has restored their laptop volume control buttonsr.

A second is to install the new kmilo from the new Hardy repositories.  Supposedly, this is a newer version of kmilo and perhaps wll work better.  I have no idea how a program designed to work with the as yet undeveloped Hardy will work under Gutsy.

A third is to try to retrograde (since most buttons worked in Feisty).  There's a deb file for the kmilo that worked in KDE 3.5.6 here: [http://kenny-x.student.utwente.nl/stuff/kmilo_3.5.6-0ubuntu2_i386.deb]("http://kenny-x.student.utwente.nl/stuff/kmilo_3.5.6-0ubuntu2_i386.deb")

A fourth is to remove kmilo from automatically running (System Settings/Advanced/Service Manager and then uncheck Kmilo).  Once done, you can try to set up the volume shortcut keys in kmix global shortcut setting.

A fifth is to try applying a patch (see attached zip file).

I haven't tried any of these because I don't really use my volume buttons and so was just curious about this bug; I'm not anxious to experiment with a stable audio system.  The other reason I haven't tried them is because there is very little anecdotal evidence suggesting that they work; it seems to depend somewhat on the kind of laptop.

This bug seems to happen to many different kinds of laptops (mine is an Asus F3Jseries).  

If anyone tries one or more of these, perhaps posting results here would be helpful.

And again, if there are any developers listening (it's already in the bug report system), then please consider how many people are affected by this and perhaps move it up in the priority list.

---

### Post by Jarn on 2007-10-31
It doesn't apply just to laptops, it applies to any keyboard that hasa volume up/down button (which is what I have). Though, recently, they started to work again - I'm not sure why as I did not change anything.

---

### Post by randcoop on 2007-10-31
I used the deb file (see my previous post) for kmilo 3.5.6 and my volume buttons now work.  If you do that, you'll find that apt thinks you need to update the program (since you're using an earlier version).  To change that, you can make (or add to) an /etc/apt/preferences file.  In that file, put:

Package: kmilo
Pin: version 4:3.5.6*
Pin-Priority: 1001

And apt will stop telling you to update.

---

### Post by joao82 on 2007-11-04
> **randcoop said:**
> 
A third is to try to retrograde (since most buttons worked in Feisty).  There's a deb file for the kmilo that worked in KDE 3.5.6 here: [http://kenny-x.student.utwente.nl/stuff/kmilo_3.5.6-0ubuntu2_i386.deb]("http://kenny-x.student.utwente.nl/stuff/kmilo_3.5.6-0ubuntu2_i386.deb")


this one worked for me. thanks.
I didn't say this sooner because the first time I tried, I just double clicked on it and it seemed to install. but I later found out that installing .deb files on my gutsy with a double click only stalls the computer for a minute and leaves the application GDeby quietly. I had to turn to the terminal, install there and reboot.
I have regular keyboard sound control now.

---

### Post by BFris on 2008-02-02
I've struggled with this one,  too. I used a different solution. In the Regions and Accessibility portion of Kcontrol, you can put in some custom keys. This thread explains it well (look for the post by keinhaar):
[http://ubuntuforums.org/showthread.php?p=4167457#post4167457]("http://ubuntuforums.org/showthread.php?p=4167457#post4167457")

the downside to this strategy is that you won't get any on screen verfication that the volume is changing. But it really works quite nicely. The upside to this strategy is that when packages get updated, your volume keys won't get hosed.

---

### Post by theToolman on 2008-02-07
Using the Feisty deb fixed the 0-11% issue on my newly installed kubuntu Gutsy Gibbon.  Hardware, Acer Aspire 3680 laptop.

thanks.

---

