---
title: "intrepid upgrade issues"
date: 2008-11-02
forum: General Help
---

### Post by jalyst on 2008-11-02
I upgraded to intrepid, all seemed to go well... Then i got a prompt asking me if I wanted to install nvidia binary drivers so I decided to go ahead with it. 

There were two 173 and 177, it recommended 177 so I chose to activate it. Once the process completed it asked me to reboot, I rebooted and I've since not been able to boot back in... 

There's an initial splash screen but that's it, nothing else comes up to indicate what the problem might be...

Just FYI I'm running mythbuntu, my understanding is that the packages assoc. with it will upgrade along with the main distro.

Please don't tell me my system is hosed, is there anything that can be done?

Cheers,
Jed

---

### Post by jalyst on 2008-11-03
Anyone? 

Any advice/help would be greatly appreciated...

I'd prefer to avoid a re-installation if I can!

---

### Post by Mark224 on 2008-11-03
If you hit Ctrl+Alt+F1 you should be able to log in without the GUI.  I'm not sure what you can do from there, but hopefully someone else can help.

You could try running "dmesg" and "tail /var/log/messages" to see if there are any reported errors.

---

### Post by jalyst on 2008-11-04
tnx, just going to dload 8.10 and start afresh... Unless someone has come across this and can suggest a fix? 

It had successfully upgraded and rebooted, problem only kicked in after i activated nV binary rivers and rebooted...

-jed.

---

### Post by zeigfried on 2008-11-04
Hey

Log in the **recovery mode** (second option on grub) - Hit the esc key if this entry isn't appearing -
Choose to fallback to root terminal.

Type:
> nano /etc/X11/xorg.conf

Under the Section "Device", in the line where it reads > Driver Change whatever is between quotes ["nvdia","nvidia-glx", "nvidia-glx-legacy", "nvidia-glx-new"] to "vesa".

Press Ctrl+O, enter (to save), and Ctrl+X (to exit).

Reboot and try to log in normally.
Reinstall your drivers [Binary Driver How To / Nvidia]("http://https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

Cheers,

---

### Post by jalyst on 2008-11-04
@zeigfried:

Mate thanks heaps, you're a life saver!

It hadn't occurred to me I could try editing xorg.conf.
I edited it using vim as I'm more familiar...

I was initially thrown-off by your explanation where you say: "In the session Device..."
Then it hit me you were really trying to say: "In the 'section' Device..."

I found the offending entry and it actually said "nvidia".
I replaced this with "vesa", saved and exited, rebooted, and... Wala!

I'll now investigate why this played up, hopefully that article you link to is a good start.

If you live in my area (and you're not underage) I owe you a six pack!   :-)
Thanks Mark for your efforts too.

-jed.

---

### Post by zeigfried on 2008-11-04
OK, I'm glad I could help.
I fixed the last post for further reference.
If you ever come to Brazil we can share the beer cans and a couple of caipirinhas (google for it :D).

---

### Post by jalyst on 2008-11-07
> **zeigfried said:**
> OK, I'm glad I could help.
I fixed the last post for further reference.
If you ever come to Brazil we can share the beer cans and a couple of caipirinhas (google for it :D).

Thanks Anthony,

I googled it... perfect, I'm a big rum drinker!* 
Well I used to be in my early 20's, slowing down nowadays :)



*sounds better than 'bundaberg rum'.

---

### Post by tobiz on 2008-11-10
jalyst, I had problems with nvidia and 8.04.1. Solution was to download latest nvidia driver from nvidia linux web site, reboot into recovery mode and run the nvidia package to install, don't select the option to download their binary driver, the nvidia install builds the driver from source for your kernel (I think it's a dkms package). Using this method I had nvidia 177.80 running on 8.04.1 with no problems. I expected to have similar problems with mythbuntu 8.10 but their nvidia 177.80 driver worked for me, I didn't select the binary driver at the 8.10 install for the reasons above.

---

