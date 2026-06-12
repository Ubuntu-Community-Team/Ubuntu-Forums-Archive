---
title: "Asus EB1501P IR XBMC"
date: 2010-10-28
forum: Hardware
---

### Post by ehowe01 on 2010-10-28
I just picked up this device with the goal of putting Ubuntu 10.04/XBMC  on it.  Ubuntu does not see the IR receiver at all, and thus the remote  does not work.  I followed the guide at  [http://wiki.xbmc.org/index.php?title=HOW-TO_perform_a_miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501](http://wiki.xbmc.org/index.php?title=HOW-TO_perform_a_miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501)  and also attempted the method for the German / Asian version.  Nothing  so far has worked.

Lspci does not see the receiver, dmesg and /var/log/messages don't seem to detect it either.

I  know this is a new device and probably hasn't been tested out much yet,  but I figure I must not be the only one trying to get this to work.

I  was thinking about upgrading to 10.10 to see if that would help out at  all, but I thought I would post here first to see if anybody has any  ideas.

[UPDATE]
I reinstalled last night with 10.10, still no IR receiver.  I'm running out of ideas here.  Anybody got anything?

---

### Post by senilio on 2010-11-01
Please note that the IR reciever is now located here:

/sys/devices/pnp0/00:0a

On previous versions of the eb1501 it used to be found at 00:09.

---

### Post by ehowe01 on 2010-11-01
That's what I thought.  I've tried echoing activate into /sys/devices/pnp0/00:0a/resources and it changes its state to active, but it still doesn't show up in lspci, and it still doesn't respond to the remote.

---

### Post by senilio on 2010-11-01
I too followed the "German / Asian" guide.

Only difference seems to be I did a *dpkg-reconfigure lirc *and put *Windows Media Center Trancievers/Remotes *under "Remote control configuration", and *Custom *under "IR transmitter".

Other than this, I followed the guide.

---

### Post by ehowe01 on 2010-11-01
Thanks, I'm giving that a shot now.  I had the remote set the same, but I used none for the ir receiver as the guide said.  I'll post back with my results in a few.

---

### Post by ehowe01 on 2010-11-01
Hmm.  No luck there.  Still nothing when I run irw.  Did you end up using the start_ite8713 script?  I've tried it both ways, still nothing.  The receiver should show up in lspci after activating it, correct?

---

### Post by senilio on 2010-11-01
Yes, I am using the start_ite-script. I ended up modifying it a bit. Perhaps you'll have better luck following my little guide a wrote on the xbmc forum:

[http://forum.xbmc.org/showpost.php?p=635064&postcount=115](http://forum.xbmc.org/showpost.php?p=635064&postcount=115)

Please let me know your results.

BTW, nothing shows up for me in lspci or lsusb, so I don't think you should worry about that :)

---

### Post by ehowe01 on 2010-11-01
You, my friend, are a lifesaver.  That worked.  It is definitely the IRQ problem.  Using your template and modified script did the trick.  Will mark this post as solved.  Thanks for all your help.

---

### Post by senilio on 2010-11-01
Glad I could help! If you run into any other problems with your eb1501p, I might be able to help... good luck!

---

### Post by dredmond on 2010-11-03
Hi, as far as I can tell I've followed your instructions to the letter but I still can't get the remote going on my new 1501P :(

Is there any logs/commands I can use to figure out where I've gone wrong?

TIA :)

---

### Post by ehowe01 on 2010-11-20
Sorry for the late response, were you able to get it up and running yet?  If not, make sure that the start_it8713.sh script is executing on boot, and it should look like this:

echo activate > /sys/devices/pnp0/00:0a/resources
sleep .2
NEWIRQ=$(grep ^irq /sys/devices/pnp0/00:0a/resources|cut -d' ' -f2)
TEMPLATE=/root/lirc.template
TARGET=/etc/modprobe.d/lirc.conf
cat $TEMPLATE | sed 's/GETIRQ/'$NEWIRQ'/g' >$TARGET
/etc/init.d/lirc stop
rmmod lirc_it87
echo activate > /sys/devices/pnp0/00:0a/resources
modprobe lirc_it87
/etc/init.d/lirc start

lirc should not be set to start on boot, check rc.d for that as well.

---

