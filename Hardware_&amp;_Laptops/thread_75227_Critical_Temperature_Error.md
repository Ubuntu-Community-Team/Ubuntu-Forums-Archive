---
title: "Critical Temperature Error"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by Bondolon on 2005-10-13
It keeps telling me that Critical temperature has been reached, and refuses to keep booting.  However, that ISN'T the case, because I had the laptop sitting on my lap, and I think I would find it odd that my skin suddenly started burning.  The laptop isn't very hot at all.  It's a compaq V2000.

---

### Post by jxn on 2006-02-09
I'm having this same issue; any fix yet?

---

### Post by dockingman on 2006-02-10
Same thing here, laptop (Toshiba Satellite A10 - Celeron 2.2) keeps on turning off suddenly with no apparent reason... log says something about critical temperature reached, but not always...

---

### Post by slavik on 2006-02-10
I have the v2000z and when it did turn off with that error, the latop was pretty hot.

---

### Post by bgoody on 2006-02-10
[QUOTE=Bondolon]It keeps telling me that Critical temperature has been reached, and refuses to keep booting.  However, that ISN'T the case, because I had the laptop sitting on my lap, and I think I would find it odd that my skin suddenly started burning.  The laptop isn't very hot at all.  It's a compaq V2000.[/QUOTE]

Hi.  I had the same problem.  It turns out it was something to do with acpi. I had to reinstall.

However, to confirm that it is something in your installation and not a physical reality, do what I did and boot from a live cd to see if it stabilizes your system.
Brian

---

### Post by mentat on 2006-02-10
Hi. I'm running Ubuntu 5.10 on an Acer TravelMate 4002WLMi, and the same message appears when I shut the laptop down ("Critical temperature reached, 144 degrees"), even if it was turned on for a few minutes. I am sure that this is not the correct temperature... This only happens since I upgraded the kernel to 2.6.12-10-386. Apart from that message upon shutdown, I don't notice anything strange since the upgrade. Maybe it's a bug?
P.

---

### Post by jakemikey on 2006-02-20
I have this same problem on my brand new Compaq Presario V2555US.  The symptom on mine is that the battery monitor applet shows as being plugged in (though it's not) and displaying an "N/A" instead of the % charge.  The mouseover says that it is running on AC power and that there is no battery present (though obviously there is).  The laptop is not any hotter than normal operation and I can hear the fans running.  Suddenly X will crash and I get the "critical temperature error" and the laptop shuts down.  The only thing that clears this problem out for me is booting quickly back into Windows and then back into Ubuntu.  The problem then goes away for a while, but ultimately comes back and I have to do the process again.

This is obviously not a hardware problem - at least that's what my symptoms tell me.  I mean, if Windows runs fine afterwards I can't imagine its really overheating.

Any solutions?

---

### Post by waxbolt on 2006-02-22
I had the same problem installing ubuntu on an old Gateway Solo.  Turned out that booting the installation with the acpi=off option removed the problem.  Unless you really need the battery save options and thermal readings that acpi provides, this simple fix might tide you over until the deeper issues are resolved.

---

### Post by handy on 2006-02-22
Ditto!!

**[EDIT:]** I should be more specific & say that, I found this problem on a **Winfast K7S741MG** board.

I could not install Ubuntu without the acpi=off parameter!?

---

### Post by bartenst on 2006-02-22
Having the same problem with my HP Nx6110 laptop :( Yesterday I upgraded to the most recent firmware but that did not improve the situation.
For now, I keep booting the laptop with the kernel option "acpi=off" - but that is just a temporary workaround.

---

### Post by bartenst on 2006-02-22
Interestingly enough, after having booted from the Kubuntu Live CD *once* the kernel boots without any problems. How comes?

---

### Post by Skye on 2006-02-22
I had this problem on my Compaq v2402us, but I fixed it by upgrading to the 2.6.15.1 kernel, and applying the 2.6.25.2 acpi patch to it.  The acpi patch can be found [here]("http://ftp.kernel.org/pub/linux/kernel/people/lenb/acpi/patches/release/2.6.15/acpi-release-20050902-2.6.15.diff.bz2"), and the 2.6.15.1 kernel is [here.]("http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.15.1.tar.bz2")

If you need to know how to compile a kernel, use the steps related to kernel compilation from this how-to, but ignore the stuff related to suspend2:
[http://ubuntuforums.org/showthread.php?t=75443]("http://ubuntuforums.org/showthread.php?t=75443").

Be aware that running a non-Ubuntu kernel posed problems in terms of interoperability with the rest of Ubuntu.  There may be other ways to fix this, but I don't know of them.

Good luck!

---

### Post by bartenst on 2006-02-22
Skype, thanks for your reply! As a former Gentoo user I know how to compile a new kernel. But having to compile everything made me switch to Ubuntu Linux and I kind of do not want to go back to these times. Maybe the next Ubuntu kernel comes with some ACPI fixes that make the problem go away? At least I hope that this will happen. :)

---

### Post by bartenst on 2006-03-05
Any news regarding this issue? From time to time I have to boot with the Live-CD in order to be able to boot up the most recent kernel without shutdown.

---

### Post by Skye on 2006-03-05
The problem appears to be fixed in Dapper, as I didn't have to do any funky patching of the kernel- it Just Works (TM).  I don't know what the status is in Breezy, though.

---

### Post by EviL_SmUrF on 2006-03-06
i can tell you right now it's not fixed in breezy. just installed it on my brand new compaq v2000z (amd sempron processor) and it overheats to 144 C then shuts down. no cpu fan coming on at all.

very, VERY frustrating and annoying.

im downloading dapper right now to see if installing it clean on it fixes the problem. i really would like to have a functional cpu fan on my laptop

---

### Post by patrickfromspain on 2006-03-06
[QUOTE=mentat]Hi. I'm running Ubuntu 5.10 on an Acer TravelMate 4002WLMi, and the same message appears when I shut the laptop down ("Critical temperature reached, 144 degrees"), even if it was turned on for a few minutes. I am sure that this is not the correct temperature... This only happens since I upgraded the kernel to 2.6.12-10-386. Apart from that message upon shutdown, I don't notice anything strange since the upgrade. Maybe it's a bug?
P.[/QUOTE]
same problem with a toshiba L10-161. However... it doesn't bother me much, as the notebook goes just fine.

---

### Post by bato on 2006-03-06
I had the same problem on my hp compaq nx6125, the fan come up only when the processor was very hot (over 80 °C). So when the processor temperature goes over 60 °C you can try to type "acpi -t" command in a terminal. If the fan come up you can follow this post to workaround the problem.

[http://ubuntuforums.org/showthread.php?t=130936](http://ubuntuforums.org/showthread.php?t=130936)

Obviously it's a workaround and I hope new kernel solves this problem.

---

### Post by hollowhead on 2006-03-06
I have a hp nx6110 and do not have this problem.  I have used it for some hours at a stretch.

---

### Post by EviL_SmUrF on 2006-03-06
it's so freaking annoying =) 

/proc/acpi/fan is empty so the laptop essentially has no way of cooling itself. 

also polling_frequency has "disabled" in it. 

ive given up and im installing suse now =S

---

### Post by towsonu2003 on 2006-03-06
you all need to file a (single) bug at [https://launchpad.net/malone](https://launchpad.net/malone) to let the developers know something is wrong. 

I have found the following bugs, take a look, and post comments and subscribe to them if you feel one is actually what you are experiencing: 

[https://launchpad.net/distros/ubuntu/+bug/22336](https://launchpad.net/distros/ubuntu/+bug/22336)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/9791](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/9791)
[https://launchpad.net/distros/ubuntu/+source/acpi/+bug/11768](https://launchpad.net/distros/ubuntu/+source/acpi/+bug/11768)

last two are rejected, one of them is rejected due to lack of response. the first one seems to be very similar to yours.

---

### Post by Bondolon on 2006-03-16
I actually ended up getting this to work properly, and without anything insane, besides just a regular install.  I think that letting the new update for acpi-support download is the problem.  Just use the one that comes pre-installed.

---

### Post by HighTemplar on 2006-03-26
Hey everybody. Newbie with Linux (in general, not just Ubuntu) here.
I got this distro from a friend and gave it a try. The result: the best i've ever tested because of it's ease of use and hardware database. It recognized every piece of HW in my desktop and in the laptop (except for this ACPI issue). I tried disabling acpi at the command line in GRUB and appears to work. The laptop gets warm but i can't assure if it's really hot. However im downloading an update to ACPI. Hope it works!

Greets

---

