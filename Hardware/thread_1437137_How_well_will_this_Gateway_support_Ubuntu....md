---
title: "How well will this Gateway support Ubuntu..."
date: 2010-03-23
forum: Hardware
---

### Post by whiskey.will on 2010-03-23
Ok, I have a GateWay MP8708 and there was a recall on the battery issued with my laptop.  I have applied for the recall and come to find out that they don't have the battery replacement anymore so, they (gateway) has offered me a brand new laptop (nv7915u) for free (well I have to send them my current one)...  

Here are the specs for the nv7915u:
[http://www.gateway.com/systems/product/529668369.php](http://www.gateway.com/systems/product/529668369.php)

and here is the link for my current laptop:
[http://support.gateway.com/s/Mobile/Q106/SonicC/1013924Rsp5.shtml](http://support.gateway.com/s/Mobile/Q106/SonicC/1013924Rsp5.shtml)

This is obviously a great upgrade, I'm just wandering how well this laptop will support Ubuntu 9.10 64-bit.  I have just recently given up on windows and this will come with the new Windows-7 which I have no experience with.

So please, let me know what you think (especially if you have the new model GateWay)...

---

### Post by khelben1979 on 2010-03-23
I think you'll just haveto install Ubuntu 64-bit to find out. Looks like a nice upgrade from your present laptop. Linux will definitely like the 4 GB of RAM which is inside.

---

### Post by TBABill on 2010-03-23
You should have an awesome experience with that laptop. The only thing you may have to play with is the wireless adapter since I don't see a wireless adapter brand listed, but that's not normally a show stopper. I just bought a Dell similarly equipped and it's fast in Win 7...almost as fast as my old Acer with Lubuntu :) If you install Ubuntu you should be good to go. That processor (Intel i3) has the graphics processor on-board and the machines I have experience with run well on Ubuntu with Intel graphics chips.

---

### Post by whiskey.will on 2010-03-23
Thank you both for the recommendation, I'm only leery because it seems to be a "too good to be true" thing for a free brand spankin` new laptop with all that it has...

When I do make the switch, is there a way to create an ISO of my current harddrive and install it onto the new one?

---

### Post by khelben1979 on 2010-03-23
> **whiskey.will said:**
> When I do make the switch, is there a way to create an ISO of my current harddrive and install it onto the new one?

I would advice you to do a fresh install once important files from your present system has been backed up.

---

### Post by coffeecat on 2010-03-23
> **whiskey.will said:**
> When I do make the switch, is there a way to create an ISO of my current harddrive and install it onto the new one?

You can use a live CD to create one tar.gz file of your root partition with the tar command. (I use this for system backups.) And then tar in a live CD to unwrap the tar.gz into your new root partition in the new machine.

But... You then have to edit /etc/fstab to take account of the changed partitition UUIDs. You also have to do something about grub. With legacy grub it was a simple matter of editing menu.lst from the live CD and installing grub to the mbr of the new machine's sda. But with grub 2 I guess you'd have to chroot into the untarred root partition and run 'sudo update-grub' to regenerate grub.cfg with the correct UUIDs. And then install grub to the MBR.

So - it may be quicker simply to reinstall as the previous poster said.

---

### Post by Muzer on 2010-03-23
tar.bz2 will save a lot of space, but take more time.

tar -cvjf file.tar.bz2 place_to_backup_from

---

### Post by mcwho on 2010-03-28
Just wanted to let you know that I have this Gateway nv7915u. I posted [here]("http://ubuntuforums.org/showthread.php?p=9012445") regarding support for getting 9.10x64 up and running. I have not gotten the audio working nor the brightness adjustments working as I posted. Also I am not sure if it is the new kernel but every time I seem to be doing something important on the Internet the machine locks up and has to be hard reset. This happens usually in Firefox when I open a new tab and start to navigate to a new site as for some reason Chrome has been acting all crazy when trying to use Google services, email and docs, lately for some reason. The Google fiasco with Chrome is not limited to this machine but also happens on more stable machines I have been running solid for months.

I am a little disappointed to read Intel Arrandale support will not be official until kernel 2.6.33. I have not done much to modify and configure. Seems like once I got the graphics working at the native LCD resolution I just have not found the time to get everything working...

Another note is that this machine runs extremely cool. The keyboard never gets hot and the underside remains cool as long as the exhaust vent stays unobstructed. I have the CPU Frequency Scaling Monitor running on my panel and it stays at 933 MHz for the most part so I am sure that has something to do with it. But I returned a Dell Dimension XPS 16 because it ran hot and the fan never turned off. It also had ATI dedicated graphics with a TDP of 35W so this is not really a fair comparison.

I want to note though that I found many of the laptops I looked at ran hot. For some reason this Gateway runs very cool. One of the coolest I have used in many years. It is certainly a no frills basic laptop but does have a 1600x900 resolution which is tough to find in most inexpensive laptops.

As other reviews have noted the mouse button is really bad. For $600 I can live with it.

---

### Post by whiskey.will on 2010-04-04
So I have received the Gateway nv7915u and installed Ubuntu 9.10, it's going well except for a few things. [[PLEASE SEE THIS THREAD]]("http://ubuntuforums.org/showthread.php?p=9074652#post9074652") 

In response to MCWHO,
     This machine is running very cool but did you encounter the resolution problem I have posted in the above thread or have you figured out the audio problems?

---

### Post by mcwho on 2010-04-04
Did you follow the [link]("http://ubuntuforums.org/showthread.php?p=9012445") I posted to another thread which details upgrading the kernel and Xorg for getting Arrandale graphics support? Here is the [page]("http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10"). 

With mine there actually was sound but only on the headphone jack. To get audio through the built in speakers you can add "model=3stack-dig" to the bottom of your /etc/modprobe.d/alsa-base.conf file. Though this then disables the headphone jack from working.

As for the fix... I am working on it. You can follow this [thread]("http://ubuntuforums.org/showthread.php?t=1427902"). The only problem is that the upgrade scipt restore feature for Alsa does not work for custom kernels. I downloaded the source from [Realtek]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs") and am working on getting it to compile...

Let me know how it goes for getting it working...

---

### Post by mcwho on 2010-04-04
I forgot to answer the first question directly as it is kind of implied. Sorry... As soon as I finished the instructions and rebooted for Arrandale graphics support it automatically detected the correct resolution of 1600x900... Also I upgraded Chrome to a newer version and the issues have gone away regarding being able to access Google services like Gmail. Therefore I have not had lockups anymore as I am not using Firefox.

Audio volume controls work fine. Brightness controls do nothing still.

---

### Post by whiskey.will on 2010-04-04
mcwho THANK YOU for responding to this [[THREAD]]("http://ubuntuforums.org/showthread.php?p=9075300#post9075300")...  [This]("http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10") worked perfectly for the resolution problem, I'm about to start on the audio.  Let's hope it is just as easy for a "new-buntu" user...

---

