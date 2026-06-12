---
title: "Intel D945GCLF2 Motherboard: Unable to use suspend-to-RAM, resume broken?"
date: 2008-12-02
forum: Hardware
---

### Post by Master One on 2008-12-02
I am using an Intel D945GCLF2 motherboard with the dualcore hyperthreading Atom 330 processor.

Everything seems to be working fine so far, except suspend-to-RAM.

Suspend-to-RAM (ACPI S3) is explicitly supported by that motherboard, I just upgraded to the latest BIOS version (0122), power-management-option in BIOS "ACPI Suspend" is set to "S3 State" (the other selectable option is "S1 State").

Testing with Ubuntu 8.10, once I initiate pm-suspend the computer is gone to sleep within a few seconds, and it's definitely correctly sleeping (and not just off), because it can be woken up by pressing any button on a connected PS/2 keyboard (in addition to using the power button), which is not the case, if the computer is powered off (then it can only be switched on with the power button).

The problem is now, that it can not be woken up correctly. Once a button on the keyboard or the power button is pressed, I can see the LED on the CDROM drive flash several times (as if it's searching for something on a CDROM), and after a few seconds the computer starts to boot normally, as if it was not sleeping, but just switched off.

It kind of seems, as if the kernel segfaults on resume and then resets the machine, which results in a normal boot, but I can't really tell, because during the failed resume I have no output on screen, and then it is just followed by a normal boot process.

I understand, that such a problem is very hard to debug, because it just can not be analyzed, what's going on during such a failing resume. I already searched the web, and found the [Sleep Quirk Debugger Page](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-advanced.html). I followed the shown instructions:```
echo 1 > /sys/power/pm_trace
pm-suspend
```but checking dmesg after a failed resume and following reboot just gives this:```
$ dmesg | grep -i matches
[    2.836980] bdi 1:15: hash matches
```and I have no idea, what that means (it does not look like the example shown on the mentioned webpage).

Can anybody with an Intel D945GCLF or D945GCLF2 motherboard please check, if suspend-to-RAM results in the same problem on resume, as described, and report back?

I am confident, that this is a general issue, because I tried it with a stock Ubuntu 8.10 installation (minimal-install using the alternate CD with "install a commandline-system"), and the Ubuntu 8.10 Desktop LiveCD (both 32bit). It's just strange, that I could not find any info on resume problems for that motherboard searching the internet.

P.S. I also filed a bug-report on launchpad, please see bug [#304457](https://bugs.launchpad.net/bugs/304457).

---

### Post by executor on 2008-12-02
did a quick test and it sems, that suspend to ram work her, a password screen popt up and things was back. onely wifi don`t come up.


its`s a D945GCLF2 whit 2GB ram.

---

### Post by Master One on 2008-12-02
Now that comes kind of unexpected, because that would mean, it's not a general issue, and also would explain, why I could not find any info on any resume problem on the net.

Please be so kind and have a look at the following questions:

(1) Which BIOS version is on your motherboard? Mind has the latest 0122, full BIOS string as shown on the BIOS main page: LF94510J.86A.0122.2008.1117.0113

(2) When you turn on your computer, do you see a screen with a graphical logo, before the boot-process starts, with something like "Press F2 for BIOS"? Because I don't see a graphic or the F2 prompt, instead the screen stays black, then I see "94" followed by "00" in the lower right corner, which means the keyboard buffer has been cleared followed by ready-to-boot.

(3) What's your video configuration in the BIOS advanced system setup? I have selected the following:```
DVMT Mode: <DVMT>
IGD DVMT Memory: <Maximum DVMT>
IGD Aperture Size: <256 MB>
Primary Video Adapter: <Int Graphics (IGD)>
```

(4) Do you have anything connected to the IDE port? I have just a slim CDROM burner on IDE, the HDD is on the first SATA port.

I also have 2GB RAM installed, memory configuration in BIOS left at <Automatic>.

The other things I changed in BIOS (which surely do not have anything to do with the described issue):```
HPET: <Enable>

ASF Support: <Disable>

After Power Failure: <Last state>
Wake on LAN from S5: <Power on>
ACPI Suspend State: <S3 State>
Wake system from S5: <Disable>
Keyboard Select: <Keyboard 1>
```
There is nothing else, that can have an influence.

I will now perform a new installation of Ubuntu 8.10 and do more tests. I will also install the latest BIOS version once again.

I really need suspend-to-RAM to work, it's one of the must-have features.

---

### Post by executor on 2008-12-02
1 LF94510J.86A.0099.2008.1117.0303, i have ann older BIOS then you.

2 the same as you "94" followed by "00". i only se the graphical log
when i hit the F2 att boot.

3 adjusted my BIOS to same settings you have, suspend to ram still work her.

4 i have a slim dvd, 40 pin IDE to SATA converter, so i don`t use the IDE port, SATA 2.5"hdd

---

### Post by Master One on 2008-12-02
> **executor said:**
> 1 LF94510J.86A.0099.2008.1117.0303, i have an older BIOS then you.
I guess, that's the one version, that was installed, when you got the board. There have been two new versions in the meantime, after 0099 it was 0103, and now it is 0122. AFAIK from the release-note, nothing drastical has changed, so I guess if it's working with 0099, it still should with 0122.

> **executor said:**
> 2 the same as you "94" followed by "00". i only se the graphical log when i hit the F2 att boot.
In the meantime I have found out, that this behavior is normal. The board is too fast with booting to show the graphical logo, and it's mentioned on the Intel website, that if it has to be shown, the harddisc pre-delay (usualy set at "0") should be set to a higher value, which I just tried, and it was showing the logo and "Press F2 for Setup" message then.

> **executor said:**
> 3 adjusted my BIOS to same settings you have, suspend to ram still work her.
And you definitely tried "suspend" aka suspend-to-RAM, and not "hibernation" aka suspend-to-disk? Because I just checked, hibernation is working as expected, so only suspend-to-RAM is causing problems here.

> **executor said:**
> 4 i have a slim dvd, 40 pin IDE to SATA converter, so i don`t use the IDE port, SATA 2.5"hdd
I just tried with PATA disabled in BIOS, and even disconnected the IDE cable and power supply to the slim DVD burner, but that did not change anything.

I was fiddling around with that matter the whole evening, and I am running out of options. I tried all that came to my mind, reflashed the actual BIOS (0122), reseted the CMOS data (by pulling the CMOS battery), applied setup defaults to BIOS settings, exchanged the 2GB MUSTANG DDR2 667MHz memory against 2GB KINGSTON DDR2 667MHz (although both are confirmed to be working with that board), performed a completely new Ubuntu 8.10 32bit installation from the Desktop CDROM + full system update afterwards, and still the same problem: the system seems to suspend properly, but on resume first it takes some time (with the LED on the slim DVD drive flashing) and then it boots normally, if just have been switched on.

As already mentioned, hibernation and resume from hibernation works as expected, so it really is only about resume from suspend-to-RAM.

As nothing else seems to make any sense, I'd say, blame it on the BIOS version 0122 (vs. your working 0099), then I'll have to send a support request to Intel (which must likely will result in nothing at all).

If anybody reading this has any additional ideas, please tell, I am really desperate. :(

---

### Post by executor on 2008-12-02
yes i use the system->shut-down->suspend.

"suspend" aka suspend-to-RAM

---

### Post by Master One on 2008-12-02
executor, you wouldn't want to try the BIOS update to version 0122, to see, if it is still working then?

Somehow I can not believe, that this is a BIOS issue, as usually problems get fixed with newer BIOS releases, not the other way around.

If it's not the BIOS, nor the system memory, maybe the power supply? What else can cause a resume to fail that way?

P.S. I already have sent a support request to Intel, and it will be interesting, how this is turning out.

---

### Post by executor on 2008-12-02
i wil flash the BIOS tomorrow

---

### Post by Master One on 2008-12-03
Thanks a lot, executor, this will be of great help. This issue is really driving me crazy.

---

### Post by executor on 2008-12-03
ok have flash the BIOS to v0122, suspend to ram still works her,

when you shutdown your computer do you have a green ligthe on the motherboard? if not, then the motherboard is not getting +5v standby power.

[http://download.intel.com/support/motherboards/desktop/d945gclf2/sb/e45013001us.pdf](http://download.intel.com/support/motherboards/desktop/d945gclf2/sb/e45013001us.pdf) 

se page 34-35-36

---

### Post by Master One on 2008-12-03
Thanks for trying, I guess that means it's not a bug, and should generally be working just fine, so this issue is limited to my setup only.

I already suspected the power supply (since it's a PicoPSU), but the green onboard standby power LED above the power connector is on at all times, so even when the computer is turned off, as well as when going to suspend, and during a failing resume.

I'll nevertheless will try a normal fullsize power supply as well, but if that also does not change anything, the last option is to assume that this motherboard is faulty, and has to be replaced.

I'll close the opened bug for this issue now, and will report back with further results.

---

### Post by Monkey Nuts on 2008-12-10
Thank god, i'm not alone!!

I also have the Intel D945GCLF2 and have been experiencing problems similar to the ones you have described. The system i've put together is:

* Intel Dual Core Atom 1.6GHz Mini-ITX D945GCLF2 Motherboard
* Corsair 2GB DDR2 667MHz/PC2-5400 Memory Non-ECC Unbuffered CL5
* Western Digital 320GB 2.5" Hard Drive Scorpio Black SATAII 7200rpm 16MB Cache
* Sony NEC Optiarc AD-7633A - DVD±RW (±R DL) / DVD-RAM drive - IDE
* Happauge WinTV Nova 500 Tuner
* picoPSU-90 DC-DC ATX power supply (90 Watt) and 80W AC Universal Adapter

I originally built the system to run Ubuntu 8.10, with a view to running MythTV as a media PC. Ubuntu ran fine, but I struggled with MythTV (bad tearing on playback of TV). Consequently, I gave up before I ever got round to trying the sleep function in Ubuntu. Now, I know it's not big and I know it's not clever, and I hang my head in shame as I write this, but i've gone over to the other side and bought Vista. All playback problems solved but i've encountered the sleep problem that you describe.

In brief, I can get Vista to sleep (S3, confirmed in BIOS) but nothing I do will get the PC back to the OS again. If I hit the keyboard, or the power button, the system powers-up, i.e. fans come on, lights come on, drives spark to life, but then I'm left with a blank screen and no further activity. I have to cold-boot to get the PC back again.

Here's some of the things i've tried to get round it:

* I've booted from an Ubuntu Live CD and tried sleep from there - no good.
* I've stripped the PC down to bare minimum (at Intel's support desk suggestion) with a view to reducing the power requirements of the board - * no good.
* I've tried the latest version of the BIOS, plus revisions 0103 and 0099 - no good.
* I've fiddled with every setting I can find in Vista - no good.

The OS seems to acknowledge that the motherboard supports S3 sleep mode, i.e. the "powercfg -a" command reports that S3 sleep state is supported and SiSofts Sandra Benchmark app shows support for S3 sleep.

I currently have a support call open with Intel and I seem to have finally got past the "have you tried turning it off and on again?" type questions and have been put through to a regional (UK) helpdesk.

I'd be very interested to know if you've got any further with this and i'm happy to post anything sensible that Intel pass on to me.

Have you tried switching the power supply yet? What happened?

---

### Post by Master One on 2008-12-10
The only similarity seems to be the picoPSU, and that's still my major suspect. I was too busy since last week to go on with this, but I have two different additional power supplies here to try, one is  a full-size ATX-PSU, and another 60W DC-DC + AC-DC adapter kit from a miniITX chassis.

Since I already switched the system memory to a different brand one (and both are known to work with this kind of motherboard), disconnected the optical drive from the IDE port, and BIOS version is also confirmed to be not responsible for our problem, the only thing that's left is the power supply. Maybe the picoPSU does not offer enough or too unstable juice on the 5V line when in S3 mode to power the RAM (although the green onboard LED still lights as bright as always). If it's not the PSU, I have nowhere to go, and the only possibility left to assume is, that my motherboard is defective (then your's would most likely suffer a similar problem).

I'll look forward to test the two other PSUs within the next few days, and report back here. If you find out anything in addition to that, please do the same.

---

### Post by Master One on 2008-12-13
I can confirm now, that it's the picoPSU causing these ACPI S3 Sleep problems!

I swapped the picoPSU-90 for a fullsize ATX power supply, and ACPI S3 Sleep worked just fine with the D945GCLF2 motherboard.

The issue seems to be general one, so not limited specifically to my picoPSU unit, because I also tried another picoPSU-90, and it is showing exactly the same problem. Of course I also tried swapping the AC-DC adapter, but that had no influence, so it definitely is the DC-DC part (= picoPSU-90 unit).

That's pretty bad, because I do not have any other power supply, that would fit into the used chassis, so it looks like I'll have to stick with hibernation instead of suspend-to-RAM (unless I find a PSU small enough and ACPI S3 Sleep able).

I'll write a support-request to mini-box.com now, they surely should have a clue about this. I'll report back, as soon as I have an answer.

---

### Post by Monkey Nuts on 2008-12-14
Good news, in a way. It's not good that it doesn't work, obviously, but it's nice to know what's causing the problem. I'll see if I can borrow a full size ATX power supply from work tomorrow. I'll post the results when I get to give it a try.

Given that the picoPSU doesn't seem to work, and I have a case that isn't going to take anything much bigger than a picoPSU, I don't suppose you can recommend a suitable alternative?

---

### Post by Monkey Nuts on 2008-12-16
[FONT=Tahoma][SIZE=2]Had a bit of an update from an eBay seller (fullspeedit) who specialises in these things. His response is :[/SIZE][/FONT][SIZE=2]

[I][FONT=Tahoma]There was a modification made in August to increase compatibility with some boards. You can tell if your PSU is one of the upgraded units by finding C4 on the board (same side as the HD power output header, directly beneath it between 2 x ICs). On modified units it should stand proud of the ICs due to an extra capacitor piggybacked to the original one. I do have details of the modification if you have a very steady hand and the ability to work on surface mount devices!

[/FONT][/I][FONT=Tahoma]I asked for a bit more details and he replied with:

[/FONT][/SIZE][SIZE=2][COLOR=Black][I][FONT=Tahoma]Pull the PicoPSU off the motherboard and then remove the output lead that goes to the hard disks. Directly beneath the white connector you'll see two black squares (ICs) with two components between them. Below one of these components you should see 'C4' in white print on the board. If the component labelled C4 is level or slightly proud of the height of the ICs then it's the modified version and should work. If C4 is lower than the height of the ICs then it's unmodified.

[/FONT][/I][FONT=Tahoma]Anyway, i'm going to have a look later on and see if I can figure out whether mine's the unmodified version. If I need to replace it for a modified one (i'm not going to attempt the mod myself, no way!) then the seller's offered me a full refund if it doesn't work - go eBay :p

Got to say though, i've been really dissappointed with the support i've received (or not, in this case) from the vendor of the picoPSU. I bought the PSU from [www.mini-itx.com](www.mini-itx.com) and, after several emails asking for help, I haven't received a single response, not even to confirm that they've received my email - eejits!

Will update when I have some new info...
[/FONT][/COLOR][/SIZE]

---

### Post by Master One on 2008-12-16
I am very interested in this modification, which I surely can do by myself. I also sent a support request to mini-box.com, but did not get a reply yet.

---

### Post by Monkey Nuts on 2008-12-16
OK, i'll be sure to ask how the mod is done when I place the order for the replacement part (assuming that's causing the problem!).

---

### Post by Master One on 2008-12-16
mini-box.com just responded to my support-ticket:> Problem was fixed in Aug by installing a 0.1uF on top of C4. Capacitor case size is 0603. It should be pretty eacy if you have a fine tip soldering iron. Capacitor cost is very low...I'll do the mod asap, and report back here.

---

### Post by Monkey Nuts on 2008-12-16
Me too. Although, i'm not brave enough to try the mod myself (plus, I don't own a soldering iron). The nice eBay man has some of the updated PSUs' so i'm going to order one of those and sell the other on eBay, to try and recover some of my costs.

Still be interested to hear how you get on, especially if it fixes the problem.

---

### Post by Monkey Nuts on 2008-12-19
Yey!

I can confirm that, with the modified version of the picoPSU, everything works properly.

At last...

---

### Post by Master One on 2008-12-23
Good to know. I need to wait a little longer, because the necessary capacitor in SMD case is not that easy to get here. I tried to solder a standard-size capacitor, but that did not work out.

---

### Post by freekert on 2009-01-06
Hello everyone,

I just registered especially for you guys.

The case is, I own a D945GCLF2 myself which I have put in a Procase Noah ([http://www.procase.nl/details.asp?ID=662]("http://www.procase.nl/details.asp?ID=662")) and just like you I can't suspend but I can hibernate (pm-hibernate, I use Arch Linux). I just updated with no succes to the latest bios.

Now I have some questions, I'm quite the noob when it comes to hardware (this was my first self build system). I read this here on the forum:

*Pull the PicoPSU off the motherboard and then remove the output lead that goes to the hard disks. Directly beneath the white connector you'll see two black squares (ICs) with two components between them. Below one of these components you should see 'C4' in white print on the board. If the component labelled C4 is level or slightly proud of the height of the ICs then it's the modified version and should work. If C4 is lower than the height of the ICs then it's unmodified.*

Now I wonder, this problem has only to do with the picoPSU's we all use right , not the D945GCLF2? The PSU's are stuck to our cases or, at least they are separate from our D945GCLF2's, not? What do I have to pull of the mobo here then, in my case I have a ac/dc adapter, going into the case, going to a small electronic board, going via a wire to my mobo where it plugs on using a white plug. Where can I find the problem exactly, under this white plug? Any noob friendly explanation would be nice :)

Thanx guys, at least I can stop searching for the problem now but it is kind of not nice to find this as the reason for suspend not working, I was hoping for a software solution (as we all did probably).

Hope to hear from you :)

---

### Post by shardzero on 2009-01-08
> **freekert said:**
> 
Now I wonder, this problem has only to do with the picoPSU's we all use right , not the D945GCLF2? The PSU's are stuck to our cases or, at least they are separate from our D945GCLF2's, not? What do I have to pull of the mobo here then, in my case I have a ac/dc adapter, going into the case, going to a small electronic board, going via a wire to my mobo where it plugs on using a white plug. Where can I find the problem exactly, under this white plug? Any noob friendly explanation would be nice :)


Hello Freekert,

unfortunately it's not "what we all use", your Noah case as well as my Morex are not shipped with picoPSUs.
We have a seperate PSU board already installed into the case, a picoPSU looks like in this article [http://www.viaarena.com/default.aspx?PageID=5&ArticleID=483]("http://www.viaarena.com/default.aspx?PageID=5&ArticleID=483")
Which is quite a bummer 'cause we either have to buy a capable picoPSU or restart at step 2 "where to get a modification manual for our PSU".

But either way it's good to know where to start so thanks everyone for your reports.

Yours, Michael

---

### Post by Master One on 2009-01-12
SUCCESS! Finally it is also working here with my machine! Can't believe it took that long, but at first I had to wait, till our local electronic parts supplier got these tiny capacitors with case size 0603, then I modified the PSU as suggested, and it still did not work. I contacted the tech-support of mini-box again, and they told me to put another one on top of the first added capacitor, which I now did (was kind of tricky operation, because these capacitors are really tiny), and it is definitely working as supposed to.

What a relief! Suspend-to-RAM makes such a huge difference to hibernation, I really can not miss that functionality any more.

---

### Post by Master One on 2009-01-14
For reference: mini-box now uses 0.22uF on top of C4 in their latest batch of the picoPSU.

---

### Post by hinge on 2010-01-30
> **shardzero said:**
> Hello Freekert,

unfortunately it's not "what we all use", your Noah case as well as my Morex are not shipped with picoPSUs.
We have a seperate PSU board already installed into the case, a picoPSU looks like in this article [http://www.viaarena.com/default.aspx?PageID=5&ArticleID=483]("http://www.viaarena.com/default.aspx?PageID=5&ArticleID=483")
Which is quite a bummer 'cause we either have to buy a capable picoPSU or restart at step 2 "where to get a modification manual for our PSU".

But either way it's good to know where to start so thanks everyone for your reports.

Yours, Michael

Hi shardzero,

I take it that you have a mores box. Me to, have you been able to solve this.
I have exactly the same issue om two unit...

---

