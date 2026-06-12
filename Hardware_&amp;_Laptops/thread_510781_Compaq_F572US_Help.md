---
title: "Compaq F572US Help"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by LaGzo on 2007-07-27
Hey guys, I just got this laptop and switched to XP from Vista. I want to dual boot XP and Ubuntu but I can't like I do with my desktop. I've tried putting VGA=792 to load it up but it stops loading when it tries to configure the network adapter i think. Thanks.

---

### Post by LaGzo on 2007-07-27
Bump, really want Ubuntu to run.

---

### Post by fastpakr on 2007-07-27
I'm feeling your pain...

[http://ubuntuforums.org/showthread.php?t=511133&highlight=f572us](http://ubuntuforums.org/showthread.php?t=511133&highlight=f572us)
[https://answers.launchpad.net/ubuntu/+question/9882](https://answers.launchpad.net/ubuntu/+question/9882)
[https://answers.launchpad.net/ubuntu/+question/9821](https://answers.launchpad.net/ubuntu/+question/9821)

---

### Post by LaGzo on 2007-07-27
Ok I've gotten it to boot and install. Added "Linux noapci vga=792" after pressing f6. Installed and ready to go. Only problem is wireless internet doesn't work. I've tried all morning and nothing works.

---

### Post by ErusGuleilmus on 2007-07-27
Ive got a Compaq F500, and had many of the same problems that you are listing now. My laptop is pretty much at the stage that your at, the two things that I cant get to work are Compiz-Fusion or the wireless.

---

### Post by fastpakr on 2007-07-27
Where are you putting that line - menu.lst?

---

### Post by LaGzo on 2007-07-27
Nope, well I'm dual booting and when the grub menu shows up it asks what you want to boot. I press "e" and enter that at the end.

---

### Post by fastpakr on 2007-07-27
Answers my question - thanks!

---

### Post by fastpakr on 2007-07-27
> **LaGzo said:**
> Ok I've gotten it to boot and install. Added "Linux noapci vga=792" after pressing f6. Installed and ready to go. Only problem is wireless internet doesn't work. I've tried all morning and nothing works.

Are you sure about that command?  If I put:
> Linux noapci vga=792
as the last line in the list, then hit 'b' to boot, the system reboots instantly.  If I put it at the end of the kernel line, the boot process still locks.  Can you clarify exactly how you're entering this line?  Also, are you running 32 or 64 bit?

---

### Post by LaGzo on 2007-07-28
Well I'm on XP right now so I can't tell you the exact line. It's the second boot option after you press "e". When I press "e", "Linux noapci" is already there at the end of the line. I just add "VGA=792" to the end of it. So the end of the line would look like "Linux noapci vga=792". Then I press "b" while highlighting the line I added to. It should boot into Ubuntu. Hope it works! I have dual core 64bit processor but I'm running 32bit Ubuntu.

It should look something like this.
```

title		Ubuntu, kernel 2.6.19.2-custom
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.19.2-custom root=/dev/hda1 ro quiet splash Linux noapci VGA=792
initrd		/boot/initrd.img-2.6.19.2-custom
quiet
savedefault
```

Highlight the "Kernel" line and boot.

---

### Post by fastpakr on 2007-07-28
Hmm...  I can't get that to work at all, in 32 bit or 64 bit.  Curious, though - how is it that you're running 2.6.19.2?  After a base install, I'm seeing 2.6.20-15-generic for the kernel.

---

### Post by LaGzo on 2007-07-28
Oh, that's not mine. I just copied that off a random thread and added the end to it.

---

### Post by fastpakr on 2007-07-29
Hmm... I wish I could understand why that's working for you and not me.  I've tried passing those basic parameters with loaded copies of XUbuntu and Ubuntu 64, as well as with a live cd of Ubuntu 32 (all 7.04), and get hung every time.

---

### Post by Jamasony on 2007-07-29
Has anyone managed to get Ubuntu or Kubuntu to work properly on this laptop, wireless and all?  I just bought it for the sole purpose of trying Linux for the first time, after seeing a friend use it, and I think I may just return this laptop if I still can if no one has been able to do so successfully.  It's very disheartening and disappointing that I cannot get it to work (there are several similar threads scattered about with people who cannot load Ubuntu on this laptop, Compaq Presario F572US).  Anyone get it working?

---

### Post by fastpakr on 2007-07-29
I don't think anybody has everything working yet, but LaGzo at least has it booting.  With that out of the way, wireless will get resolved once somebody figures out the right driver with ndiswrapper.  If nothing else, see if you can swap the Broadcom card that came with it for a friend's Intel card - the Broadcom card is a good piece of gear for a Windows user, it's just that the drivers aren't openly available on the Linux side (yet).  You might even check eBay for a card and consider reselling yours if you can get a decent price for it.

---

### Post by Jamasony on 2007-07-29
Thanks Fast for the suggestions.  Another forum suggested adding "acpi=off" to the boot command, this worked better than anything else so far for me, and got me to where I could use Kubuntu from the LiveCD, but again the wireless card wasn't working.

Best of luck everyone...

---

### Post by fastpakr on 2007-07-29
Out of curiosity, did (or can) you try that command on an Ubuntu cd?  I'm not sure why, but on XUbuntu and Ubuntu that doesn't seem to help me.

---

### Post by fastpakr on 2007-07-29
Scratch that - I was actually able to make that work on XUbuntu.  On Ubuntu64, I have to put in 'noapci acpi=off' to get it to boot to a login screen, but at that point it continues to start looping all sounds and still doesn't get all the way to the desktop after logging in.

Closer...

Edit - I was also able to make those commands work on an Ubuntu64 live CD, but still get the looping sound and the GUI stops loading after coming to the flesh tone Human background with a working pointer.  Trying a 32 bit cd...

Same looping sound on a 32 bit CD.  Am I the only one getting that?

---

### Post by Jamasony on 2007-07-29
I didn't try it with Ubuntu.  I'm not getting any looping sound (or sound at all, for that matter).  

Edit - Do you have to have the noapic command for it to work?  Mine's just been needing the acpi=off.

I was able to do the full install with Kubuntu from the CD.  On reboot, I got an error similar to "Kernel panic - not syncing: IO-APIC + timer doesn't work! Try booting with the 'noapic' option".  I rebooted and removed the acpi=off from the kernel boot command and it's able to boot fine into Kubuntu now.

Wireless isn't up yet...  This is actually pretty amazing.  I have tried to install the Wifi driver first by looking here
[https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%281390%29](https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%281390%29)

and later tried this one,
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

On this second link, I got as far as 
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

and got an error saying that permission was denied.  I thought I'd try it this way anyway and rebooted.  And, guess what?  It hangs when loading again... at the 'configuring network interfaces' part.  Maybe it would have worked if I could have executed that command - is there another way I could have done it for it to be successful?  Back at square one now, I think I'll have to reinstall the OS over again to be able to give the wireless another attempt.

---

### Post by fastpakr on 2007-07-29
> **Jamasony said:**
> I didn't try it with Ubuntu.  I'm not getting any looping sound (or sound at all, for that matter).  

Edit - Do you have to have the noapic command for it to work?  Mine's just been needing the acpi=off.

I was able to do the full install with Kubuntu from the CD.  On reboot, I got an error similar to "Kernel panic - not syncing: IO-APIC + timer doesn't work! Try booting with the 'noapic' option".  I rebooted and removed the acpi=off from the kernel boot command and it's able to boot fine into Kubuntu now.

Wireless isn't up yet...  This is actually pretty amazing.  I have tried to install the Wifi driver first by looking here
[https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%281390%29](https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%281390%29)

and later tried this one,
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

On this second link, I got as far as 
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

and got an error saying that permission was denied.  I thought I'd try it this way anyway and rebooted.  And, guess what?  It hangs when loading again... at the 'configuring network interfaces' part.  Maybe it would have worked if I could have executed that command - is there another way I could have done it for it to be successful?  Back at square one now, I think I'll have to reinstall the OS over again to be able to give the wireless another attempt.
That's a HUGE step forward - with the 'noapic' option, the 32 bit live cd booted with no errors.  Installing now!

edit - OK, after launching the live CD with noapic, it installed cleanly and automatically inserted noapic into menu.lst.  I left the wireless card at the office, so I'll fiddle with it tomorrow if I can't trade it for an Intel from another laptop.

---

### Post by Jamasony on 2007-07-30
Great!  Good luck with the wireless.  I'll post if I make any progress.

---

### Post by fastpakr on 2007-07-30
> **Jamasony said:**
> I didn't try it with Ubuntu.  I'm not getting any looping sound (or sound at all, for that matter).  

Edit - Do you have to have the noapic command for it to work?  Mine's just been needing the acpi=off.

I was able to do the full install with Kubuntu from the CD.  On reboot, I got an error similar to "Kernel panic - not syncing: IO-APIC + timer doesn't work! Try booting with the 'noapic' option".  I rebooted and removed the acpi=off from the kernel boot command and it's able to boot fine into Kubuntu now.

Wireless isn't up yet...  This is actually pretty amazing.  I have tried to install the Wifi driver first by looking here
[https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%281390%29](https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%281390%29)

and later tried this one,
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

On this second link, I got as far as 
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

and got an error saying that permission was denied.  I thought I'd try it this way anyway and rebooted.  And, guess what?  It hangs when loading again... at the 'configuring network interfaces' part.  Maybe it would have worked if I could have executed that command - is there another way I could have done it for it to be successful?  Back at square one now, I think I'll have to reinstall the OS over again to be able to give the wireless another attempt.
The 'noapic' parameter was required in my case.  As far as wireless, I've been playing with the 'no fluff' installation from [this thread](http://ubuntuforums.org/showthread.php?t=475963).  No luck yet, but the OS still works fine.  :-)

---

### Post by fastpakr on 2007-07-30
Insult to injury...

I noticed last night that the power jack on the laptop is flaky - if I'm not careful, the cord gets jostled slightly and the blue led goes off and the laptop stops charging.  Got with Compaq on their website, and they're refusing to NOT flash the hard drive back to Vista when I mail it in for repair.  Completly inexcusable that I am required to LOSE all of my personal data in the process of having my laptop repaired because it was faulty coming out of the new box.

---

### Post by Jamie Jackson on 2007-07-30
> **fastpakr said:**
> Insult to injury...

I noticed last night that the power jack on the laptop is flaky - if I'm not careful, the cord gets jostled slightly and the blue led goes off and the laptop stops charging.  Got with Compaq on their website, and they're refusing to NOT flash the hard drive back to Vista when I mail it in for repair.  Completly inexcusable that I am required to LOSE all of my personal data in the process of having my laptop repaired because it was faulty coming out of the new box.

Do you happen to know about the "partimage" utility? It's like Norton Ghost, but free. You can run it from System Rescue CD, and it might even be on the Ubuntu Live CD.

If you've got an external drive, you can back up/restore fairly easily.

Obviously, it would be much better if Compaq didn't have to nuke your software to fix a hardware problem, but anyway...

---

### Post by fastpakr on 2007-07-30
I'll check it out.  Our version of Ghost at the office might be recent enough to support ext3, but I'd rather look for a freeware package, regardless.  Thanks for the tip.  I don't mind backing up the OS, I was just frustrated with their mindless insistence on reloading the original software image.

---

### Post by bpierce815@yahoo.com on 2007-08-09
I've got this laptop and installed Fedora7 x86_64.  Tried Ubuntu at first but gave up before adding any boot options.  Here is what I had to add to the grub.conf file to make everything work.  Append this to the line that starts with "kernel"
```
noapic irqpoll acpi=off
```
Once the Operating system is installed, turn off the cpuspeed daemon and remove "acpi=off"

Now everything should be working except CPUscaling, and in my case the laptop is on ac power most of the time anyway so it is not as big a deal for me.

Wireless:
Install ndiswrapper:
```
sudo apt-get ndiswrapper
```

Then get the XP drivers for this card:
```
wget ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe
```

Extract the driver files:
You can try 
```
unzip sp34152.exe
``` or ```
cabextract sp34152.exe
``` but I had a windows computer that I just executed this file on and then zipped the folder that it extracted.

Then install the driver into ndiswrapper:
```
sudo ndiswrapper -i bcmwl5.ini
```

Make sure that you don't have the native driver loaded or it could conflict:
```
lsmod | grep bcm
```
and if you see anything return remove the driver listed with "sudo modprobe -r **drivername**"

Double check that the driver is properly loaded into ndiswrapper and that it sees the hardware:
```
ndiswrapper -l
```

Then install the ndiswrapper module:
```
sudo modprobe ndiswrapper
```

Make sure that everything loaded correctly:
```
dmesg
```

And setup you wireless with iwconfig.

Sorry this is so long but I hope that it helps.

---

### Post by bpierce815@yahoo.com on 2007-08-09
Forgot to state the importance of removing acpi=off from the boot menu in grub.conf. 

You must remove the acpi=off option in grub.conf for the irq's to work properly.  I was able to do this by first turning off CPU Scaling in Fedora(cpuspeed service).  I don't know if cpuspeed is installed in Ubuntu by default, but if it is, you can disable it by:
```
update-rc.d cpuspeed remove
```

---

### Post by bpierce815@yahoo.com on 2007-08-10
CPU and IRQ issues with new laptops:  looks like there may be a solution Here.

[http://www.dogruel.com/index.php?op...id=46&Itemid=38]("http://www.dogruel.com/index.php?op...id=46&Itemid=38")

---

### Post by jschultz76 on 2007-08-14
I have this same laptop and have used this thread, along with the other threads and pages that were linked to in this thread, to successfully install and boot ubuntu, as well as enabling the wireless features.  However, the laptop seems to have problems sleeping (suspending).

When I try to configure the behavior through the power management app, the settings are never saved.  For example, I'll tell the laptop to go to sleep when the lid is shut, and I'll hit the "close" button.  The next time I open up the power management interface, it defaults back to having the screen go black with it is shut.  And this is indeed what happens when the lid is shut.  

Manually putting it to sleep and then closing the lid results in the laptop waking up with the lid closed.    The screen goes black, but the laptop is not asleep (or suspended).  And hibernating it takes a while.

I bought this laptop for my wife and tried to show her the benefits of ubuntu, but she keeps switching back to Vista because of the suspend/hibernate annoyance.  Any suggestions??

---

### Post by mootpoint on 2007-08-25
I followed the message above from bpierce815, and had a flawless install earlier this afternoon. One minor error: install the bcmwl5.in*f* driver into ndiswrapper, not ini as is said above. And on Ubuntu, the grub item to edit after the OS is installed is /boot/grub/menu.lst, not grub.conf. 

Also, you may want to do a minor kernel update and blacklist the open source driver, then reload the box before doing the ndiswrapper stuff. 

Thanks for doing all that work, guys, saved me a bunch of frustration!

mootpoint

---

### Post by LaGzo on 2007-09-06
> **fastpakr said:**
> Insult to injury...

I noticed last night that the power jack on the laptop is flaky - if I'm not careful, the cord gets jostled slightly and the blue led goes off and the laptop stops charging.  Got with Compaq on their website, and they're refusing to NOT flash the hard drive back to Vista when I mail it in for repair.  Completly inexcusable that I am required to LOSE all of my personal data in the process of having my laptop repaired because it was faulty coming out of the new box.

I use to have the same problem too, I just put a little aluminum foil into the AC adapters plug along the walls of the hole. Doing this makes the plug grip onto the prong thing and it shouldn't move around. Haha, kind of ghetto I know. Ehh at least I don't have to worry about the power going out when I'm away.


As for the laptop matter, I still haven't gotten the wireless working! It's a shame too, I'm stuck using Windows :[

---

### Post by faheyd on 2007-11-19
> **LaGzo said:**
> I use to have the same problem too, I just put a little aluminum foil into the AC adapters plug along the walls of the hole. Doing this makes the plug grip onto the prong thing and it shouldn't move around. Haha, kind of ghetto I know. Ehh at least I don't have to worry about the power going out when I'm away.


As for the laptop matter, I still haven't gotten the wireless working! It's a shame too, I'm stuck using Windows :[

Please see this post: [http://ubuntuforums.org/showthread.php?p=3792465](http://ubuntuforums.org/showthread.php?p=3792465)

It's working now, albeit with some work.

---

### Post by shinynew on 2008-03-31
after trying many things this finally worked 
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

