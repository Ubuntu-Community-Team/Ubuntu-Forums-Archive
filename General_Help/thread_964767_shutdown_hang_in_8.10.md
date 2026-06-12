---
title: "shutdown hang in 8.10"
date: 2008-10-31
forum: General Help
---

### Post by Ewan the moomintroll on 2008-10-31
Hi there,

a few weeks ago I installed ubuntu 8.04 and was very happy with it as my first Linux experience. The only problem was that when I shut down it the orange bar would go completely black and then hang, i had to hold down the of button to switch of.
I did a lot of googling and found that the problem has no end of potential fixes, but none of the ones i could find fixed the problem for me so i gave up and waited for ubuntu 8.10 to be released in hope that it would fix it.
It hasn't.
can anyone help?

I've also noticed that restarting my computer works fine so it's just shutting down.
My motherboard is a epox 8k5a3+.

---

### Post by Ewan the moomintroll on 2008-10-31
I should probably say that i edited "menu.lst" because of several fixes (I can't remember what I did exactly).
When i installed 8.10 it asked me if i wanted to replace "menu.lts" and i said no because i wasn't sure what it meant.

---

### Post by leifjonny on 2008-10-31
I posted this one minute ago: [http://ubuntuforums.org/showthread.php?t=965391]("http://ubuntuforums.org/showthread.php?t=965391")

same problem
dmesg is full of this:

[ 4223.986611] +------ PCI-Express Device Error ------+
[ 4223.986613] Error Severity : Uncorrected (Non-Fatal)
[ 4223.986615] PCIE Bus Error type : Transaction Layer
[ 4223.986628] Flow Control Protocol : First
[ 4223.986629] Receiver ID : 0010
[ 4223.986631] VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h
[ 4223.986633] pcieport-driver 0000:00:02.0: broadcast error_detected message
[ 4223.986636] pcieport-driver 0000:00:02.0: broadcast mmio_enabled message
[ 4223.986638] pcieport-driver 0000:00:02.0: broadcast resume message
[ 4223.986662] pcieport-driver 0000:00:02.0: AER driver successfully recovered

---

### Post by Ewan the moomintroll on 2008-11-02
just noticed that system monitor says I'm using linux kernel 2.6.24-21-generic, despite it saying that intrepid ibex should have 2.6.27 in the release notes. I should definitely fix that, so any help on how to do so would be great.

Edit: this problem is fixed, but problem persists.

---

### Post by leifjonny on 2008-11-04
Adding "pci=conf1" as a boot option gets rid of the error msges. I dont know how to make a boot option permanent though.

---

### Post by novusnix on 2008-11-04
I am encountering a problem that sounds similar to the OP's on an Acer Travelmate 4000.

My system very consistently will not shut down.  The splash screen will pop up, the orange bar will crank all the way down until it is black, then I will hear the harddrive and the CPU fan turn off.  It then sits there for a moment, and suddenly the splash screen goes away, and in the upper left hand corner of the screen it says:

acpid: exiting



I've tried a number of suggested fixes.  I've modified my stop rule in the /etc/init.d/alsa-utils to look like this:

  stop)[B]
        ifconfig wlan0 down
        ifconfig eth1 down
        ifconfig eth0 down[/B]
        EXITSTATUS=0
        TARGET_CARD="$2"
  ect ect..

(bolded portions are my additions)

I've also edited my grub menu file's default rule: /boot/grub/menu.lst: 

kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=6419e63e-a1c0-49f4-abef-f3bb1d15ec6f ro quiet splash **acpi=force pci=noacpi**

(the bolded portions are my addition).

It may be important to note that NONE of the changes made to either of these files had any effect what-so-ever.

With the grub file, I attempted both "acpi=force" and "pci=noacpi" separately.  No dice.

With regard to the alsa-utils, I attempted every possible combination of those 3 lines, including all of them alone.  No dice there either.

In my terminal, the command: *sudo ifconfig wlan0 down* has no effect.  eth1 is my wireless card.  I'm not sure if this means anything.

I have backups of all files, and know my changes, so I can unmake them easily enough if they hurt anything.

Any suggestions at all would be greatly appreciated.

---

### Post by Ewan the moomintroll on 2008-11-10
Problem is still there. Ubuntu really should fix this shut-down hang problem.

---

### Post by Ubuntist on 2008-11-10
I've got a similar problem on my Dell 8300.  With the orange progress bar shrinking to the right as per usual, the shut down proceeds until a message about shutting down ALSA appears.  It then gets stuck.  I don't think this happened the very first time I shut down 8.10, but only on subsequent shutdowns.

After the shutdown hangs up, I can get a full-screen terminal display by typing either Alt-F1 or Alt-F2; this shows the system waiting at a login prompt, but they keyboard does not work, so I can't log in.

The system monitor, by the way, says I'm using 2.6.27, as expected.

Short of a proper fix for this problem, is there a better way to turn the thing off than unplugging it?

---

### Post by gb5757870 on 2008-11-11
I have the same issue occuring on Compaq nx5000.

Good to see I'm not the only one.

EDIT: Did some poking around and this has been heavily discussed as a bug. 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995)

Scroll down to a comment by Marcos posted on 2008-11-08 which shows the solution. Hope this works for ya'all

---

### Post by lemoutonvert on 2008-11-11
Thanks.

Worked fine for me.
Straight link for lazy people: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/181](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/181) 

This has really been heavily discussed…

---

### Post by Ewan the moomintroll on 2008-11-11
No luck, my file looks different to described there.
I realize I'm not being very detailed on the problem and if there's anything I can do that might help find the source of the problem, I'd be happy to.
Sorry for dragging this forum on for so long, but it is important i get this fixed.

---

### Post by purplepaint on 2008-11-13
I'm having the problem with the message "**acpid : exiting**" being displayed when I shut down (it switches of eventually if I just leave it).  Is the fix that's been posted intended to fix this problem or just the ALSA one?

---

### Post by elctb on 2008-11-13
> **lemoutonvert said:**
> Thanks.

Worked fine for me.
Straight link for lazy people: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/181](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/181) 

This has really been heavily discussed…

This fix worked for me.

---

### Post by purplepaint on 2008-11-14
I'm having the ALSA problem now, and the fix that was posted didn't seem to help (I assume I followed the instructions correctly - my "alsa-utils" file looks like this **[http://img220.imageshack.us/img220/9167/alsafixxj2.png](http://img220.imageshack.us/img220/9167/alsafixxj2.png)**).  Is this related to the fact that I now can't get sound?

EDIT: I was able to fix the sound issue easily by turning up "master" in Alsamixer.  I don't know if it'll stick after I reboot though.

---

### Post by Ewan the moomintroll on 2008-11-14
Can't do that fix, I get this in said file:
[IMG]http://img511.imageshack.us/img511/8031/screenshotho4.png[/IMG]

---

### Post by Ubuntist on 2008-11-19
> **gb5757870 said:**
> Did some poking around and this has been heavily discussed as a bug. 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995)

Scroll down to a comment by Marcos posted on 2008-11-08 which shows the solution. Hope this works for ya'all

This mostly works for me.  Ubuntu will now shut down, but during shutdown I get the message "No VFN is running".

Commenting out```
ifconfig wlan0 down
``` in the fix has no effect: I still get shutdown and the "No VFN" message still appears.

If I comment out the other line in the fix, ```
ifconfig eth0 down
``` then shutdown hangs as before.

Any ideas on how to get rid of the "No VFN" message?

---

### Post by Ewan the moomintroll on 2008-11-22
When I start up I get a *very* brief message about acpi force off, bios sometingorother.

---

### Post by purplepaint on 2008-11-23
Am I doing something wrong with [my alsa-utils file](http://img220.imageshack.us/img220/9167/alsafixxj2.png)?

I'm using a laptop, so having it take forever to shut down can be inconvenient when I have to take it somewhere and the battery's low.

---

### Post by J@n on 2008-11-28
> **lemoutonvert said:**
> Thanks.

Worked fine for me.
Straight link for lazy people: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/181](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/181) 

This has really been heavily discussed…

Worked for me :)

Happily shutting down in no-time now!

What should I do without this excellent forum \\:D/

---

### Post by mike_judd on 2008-11-29
Renaming...
/etc/rc0.d/S35networking to /etc/rc0.d/K35networking
...(for halting) and...
/etc/rc6.d/S35networking to /etc/rc6.d/K35networking
...(for rebooting) did the trick for me.

Looks like S35networking was added to /etc/rc0.d and /etc/rc6.d in 8.10 as it didn't exist in 8.04.
As I'm pretty sure networking should be getting killed off rather than starting up when going to run level 0 or 6, I'm guessing it was either a mistake or an act of sabotage. ;)

---

### Post by StudioDave on 2008-11-29
My HP G60-125NR has this problem too. I've tried every solution that I could find on Google. None worked. The Network Manager in Intrepid won't close, so ALSA won't stop either. I have to switch off at the power strip. Very bad.

So I'm suffering the double whammy. I like so much else about 8.10, but this bug is truly ruinous. Considering the number of reports concerning it I wonder why it hasn't been fixed.

Btw: My notebook includes an nVidia 8200M, which 8.10 handles beautifully. 8.04 sucks with the same hardware, it can't even load the correct driver.

I'm not even asking for any more solutions. I'm tired of powering down my machine by the switch, and I'm very tired of trying things that don't work for me. At this point I simply want to add my voice to the growing chorus of users who are unhappy with this situation.

---

### Post by Donalb on 2008-11-29
The bugfix on Lauchpad, editing ALSA-Utils to stop eth01 works for me . Though I notice on startup now that I'm getting the line by line text display rather than graphical interface. That's obv. not important.

I'm on a new intrepid 8.10 install (yesterday) on a new Dell e6400 laptop, with Intel Corporation 82801I (ICH9 Family) sound.  
I did try one of the other fixes, starting PulseAudio manager, I think it was, killed the network connection. So I had to stop PulseAudio, then restart the wired net conn.

That said, with the shutdown issue fixed (?), I'm still without sound, (slight crackling only). Also, reading to the end of the Launchpad discussion, I see a PulseAudio "fix"??? released. Should I do this this also, i.e. installed the intrepid-proposed respoitory? Will this address the cracking sound issue?

All that Launchpad stuff is new to me, and seems to need a certain level of familiarity/expertise...

I'm reasonably happy that I encountered a SERIOUS bug, but there was fix there already once I did enough reading.
I don't understand how this receives a MEDIUM importance in Launchpad since user data loss or even hardware problems could be caused by it. I'm off to read more about understanding Launchpad now also therefore.

Also, not knowing the bug reporting situation, what should I do about adding my voice to a list of those affected so the severity is properly measured.?

Regards
Donal
Ireland

---

### Post by purplepaint on 2008-12-03
The ALSA problem seems to have been fixed with an update I received today (I was asked if I wanted to replace a particular file with a new one and I said I did).

---

### Post by Ewan the moomintroll on 2008-12-04
Didn't fix anything for me sadly.

---

### Post by hern_28 on 2008-12-11
anyone tried adding acpi=force to the grub menu.lst entry?

---

### Post by Ewan the moomintroll on 2008-12-14
Yes, I tried that but it had no effect. Would turning acpi off via bios help?

---

### Post by Donalb on 2008-12-15
And I seem to have picked up a new occasional shutdown problem.
 The 2nd step after the (fixed) ALSA problem now hangs
"Stopping AVAHI mDNS/DNS-SD Daemon". When this happens I have to hard reset.

As I say, it's irregular. I had (another) HDD crash last week (dragged one off the desk), and when transferring lots of large backup files, I was getting complete system hangs. Nothing worked to reset (not even Alt-PrntScr/REISUB) I had to hard reset each time. And was getting the AVAHI shutdown hang issue. it did not happen befoer last week.

Without the system hang the problem doesn't seem to happen As Much.

Donal

---

