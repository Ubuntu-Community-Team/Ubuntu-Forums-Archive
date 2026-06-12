---
title: "Updates of resolution od Foxconn bug --- from Foxconn FAE Heart Zhang"
date: 2008-08-02
forum: Hardware
---

### Post by zhang_heart on 2008-08-02
Hello every enthusiasts on Linux,

My name is Heart Zhang from Foxconn China, these days I and another Foxconn guy in UK names Carl Brunning contacted Ryan Farmer with each other at all times by email and phone on the big issue happened on our Foxconn MB G33M-S.

Yesterday evening I sent one debug version BIOS about this issue to Ryan, ask him to help us verify again. This morning Ryan replied me his testing result. Almost bugs are fixed by this BIOS.

Here is Ryan's testing result about the development BIOS
---------------------- 
[B]The development BIOS they sent fixes pretty much all the particularly bad behavior of the current release BIOS, in that: 

Fans resume to proper speed after resume from suspend. 

PC successfully reboots after having suspended. 

PC restarts a lot faster. 

PC no longer seems to randomly crash. 

PC hibernates and wakes up from hibernation properly. 

No longer complains about error reinitializing the Serial ATA controller. 

For the sake of curiosity, I tried booting a Ubuntu 7.10 (Gutsy Gibbon) CD, it booted up whereas it crashed before. 

Issues remaining: 

Aug  1 05:51:15 ryan-desktop kernel: [18.280909] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  96, should be 8F [20070126] 

With the release version of the BIOS it said "70, should be 69" 

Matthew Garrett says Linux doesn't even need OEMB and this is some vendor-proprietary Windows stuff. (Should be OK to ignore) 

Intel HD Audio device does not reinitialize from suspend. (Kernel 2.6.26 fixes this, it appears to be a Linux bug in kernels earlier than this, this kernel will be in Fedora 10 and Ubuntu 8.10) 

"ACPI: Error Attaching Device Data" still appears in kernel log, four times. (This too seems to be a Linux bug since 2.6.26 fixes that) 

Overall, I believe: 

The very worst of it was a bad BIOS. 

Many of the annoyances were kernel bugs that are fixed in 2.6.26.

All but the checksum error is fixed if you use the new BIOS and kernel 2.6.26, and the checksum error is not a serious issue anyway.[/B] 
---------------------- 

So it likes that the BIOS works much better with Linux.
And Ryan told me in the email, he tested the BIOS even on Windows Vista/Server 2008, there also seems like no issue.

----------------------
**I also gave this BIOS a very crude set of tests with an evaluation edition of Windows Vista/Server 2008 and it even appears to work better with a few things there.**
----------------------

If someone is intereted in this debug BIOS, you also can download from our Foxconn FAE FTP. 

[http://wft.foxconn.com/wft/Login.aspx](http://wft.foxconn.com/wft/Login.aspx)
Login: enduser
Pass: 123456

BIOS name: 772F1D43
You can unzip the file, just run flash.bat on DOS mode to flash BIOS. 
**Attention: after finishing the BIOS flashing, please goto BIOS setup to load optimized default before first time entering Linux.**

I hope you guys can get the good result that you really want.
But that is only a debug version BIOS which focus on this issue, later we will release Production BIOS for it ASAP. 
Not only on this motherboard, but also on all the other motherboards which got the same issue. 
Please make attention to our website for BIOS update,
[http://www.foxconnchannel.com/product/Motherboards/](http://www.foxconnchannel.com/product/Motherboards/)

And here I want to say Thank you to all the linux enthusiasts. From this case, Ryan and all of you gave us a lesson. And also as our plan, we will take more time on Linux OS testing. 
And I am sure Linux is becoming more popular and great OS.
For me, Carl Brunning and all the Foxconn FAE, technical support guys, we would like to receive any issues regarding to our products (motherboard and VGA card)whatever it is from Windows, Linux or any other operating system. 
You can report to this link if you have any issue or comments,
[http://www.foxconnchannel.com/support/online.aspx](http://www.foxconnchannel.com/support/online.aspx)

If possible, you can inform this message to any people as many as you can. Maybe they met the same issue before on our Foxconn motherboard. 

Thanks all of your guys' attention! Thank you very much!:KS

--- Heart Zhang from Foxconn China

---

### Post by Stratis on 2008-08-02
Awesome! 

Thanks for the update...

---

### Post by Bwosc on 2008-08-02
Wow, that's great to hear. Impressive response to the community.

---

### Post by armitage1337 on 2008-08-02
I'm highly impressed by Foxconn's rapid response to a Linux compatibility problem. This kind of attention to Linux from hardware manufacturers is highly unusual, and I applaud Foxconn for their efforts!

---

### Post by billd42 on 2008-08-02
Mr Zhang,

Thank you for your prompt and candid response to this issue.  This is exactly the kind of response the Linux community could have hoped for.  It's obvious that Foxconn is a good company that listens to feedback from their customers.  

I hope that other computer hardware manufacturers would choose to emulate your example in the future.

---

### Post by nanog on 2008-08-02
Thanks...I will remember Foxconn's quick response the next time I build systems.

---

### Post by stevoo on 2008-08-02
i think ill invest in you next time i build my newest pc !

---

### Post by Rocket2DMn on 2008-08-02
For the record, here is the bug report that was filed for this issue - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251338)

---

### Post by zooounds on 2008-08-02
My only concern is, how should we flash it from Linux?

Edit: Seems there is some kind of boot disk with some DOS-alike OS that do the job.

---

### Post by howlingmadhowie on 2008-08-02
how do you flash the bios if you don't have windows installed?

---

### Post by zooounds on 2008-08-02
> **zooounds said:**
> 
Edit: Seems there is some kind of boot disk with some DOS-alike OS that do the job. 

xx

---

### Post by MisterArcturus on 2008-08-02
> **howlingmadhowie said:**
> how do you flash the bios if you don't have windows installed?

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

FreeDOS boot CD

---

### Post by azadpanchi on 2008-08-02
Good stuff, thanks.

Viva Linux..

---

### Post by VitaLiNux on 2008-08-02
This is the kind of fast-reply one expects from manufacturers! Five stars for Mr. Zhang and Foxconn!!!:KS:KS:KS:KS:KS I'll break my promise of not buying Foxconn hardware again! After this, I can't but say thank you, Foxconn and I'll keep buying your hardware!

---

### Post by tbielawa on 2008-08-02
Awesome! I'm really pumped to see a company responding like this. I'm especially thankful to Foxconn for doing it in as little time as they did. :D

---

### Post by frup on 2008-08-02
It is good news :) Now lets hope no other mistakes like this are made, next time people won't be so forgiving.

---

### Post by ombzzz on 2008-08-02
> **zhang_heart said:**
> Hello every enthusiasts on Linux,

[...]For me, Carl Brunning and all the Foxconn FAE, technical support guys, we would like to receive any issues regarding to our products (motherboard and VGA card)whatever it is from Windows, Linux or any other operating system. 
You can report to this link if you have any issue or comments,
[http://www.foxconnchannel.com/support/online.aspx](http://www.foxconnchannel.com/support/online.aspx)
[...]


thank you very much

orlando ( from argentina )

---

### Post by Forge on 2008-08-02
Ok, two things, one good, one bad.

Congrats, Foxconn! This is a very welcomed turnaround from just a week or two ago when some tech support folks were telling us that 'Foxconn doesn't and won't support Linux on our hardware'. I sincerely hope that someone realized a hardware/firmware bug is a hardware/firmware bug, and needs to be corrected; even if it only shows up under Linux.

Additionally, I'm glad Foxconn has decided that Linux is worth supporting. That makes me decide that Foxconn is worth considering in future builds, both at home and work.



Now the bad: WTF? There's a checksum error in an ACPI table and you are NOT going to fix it?? I realize 'it only has Windows stuff in it and nothing critical', but it's also a THIRTY SECOND FIX. Unpack the BIOS, open the OEMB table in winhex, compute checksum. Not 00? twiddle the checksum bits (last two of the table) until it sums out cleanly. It takes THIRTY SECONDS. Then just repack and poof, bug fixed!

You'll probably find that this does good things for Windows issues as well. It's odd like that, bad firmware = weird issues.

If you don't have time, I'll fix it for you. It's really, really, not complicated.

---

### Post by zhang_heart on 2008-08-02
Thanks for all of you's reply.

For our Foxconn FAE FTP, there got time limitation to download stuff, the account I provided yesterday maybe expired. I just attached the debug BIOS here. You can download if you are interested in it.

You can unzip the file, just run flash.bat on DOS mode to flash BIOS after you boot your system from bootable disk.
Attention: after finishing the BIOS flashing, please goto BIOS setup to load optimized default before first time entering Linux.

Attachments as blow

---

### Post by w4ett on 2008-08-02
I'm in the process of choosing hardware for a new build....

I WILL CHOOSE A FOXCONN MOBO

Thank you.

---

### Post by serrs on 2008-08-02
I think this is great of Foxconn!  Kudos, I will try to buy your MB in the future.

I have a Foxconn P9657AB-8EKRS2H.  It's an older chipset but has (2) PCI-E x16.  I've built a multiseat box for my family around this board.

Problem!  Due to incorrect IRQ routing I *MUST* turn off USB-2.0 or I can potentially pass "irq polling" as a kernel arg.  If I don't the IDE/SATA lockup.

Otherwise it's about the highest quality MB I've come across.  Is there any hope for nasty IRQ routing issues?  (It took me about 16 hours to finally find the above workaround)

Thanks,
Scott

---

### Post by cyrex on 2008-08-02
WOW! Amazing. Well that changes my way of looking at Foxconn now. Nice work on the patch.

---

### Post by openaddict on 2008-08-02
Thank you very much for being responsive to the Linux community!  It's very well noted!

---

### Post by kjander on 2008-08-03
I think Foxconn has done really well responding to this. While I dont necessarily agree with everything that transpired as these issues were brought up, the community has shown it has a powerful voice and the BIOS writers are in the spotlight. One of the best results that can be obtained is when a company like Foxconn realizes the power of the community and becomes, not an offender, but one of the better supporters! We are definitely impressed, Foxconn. Thank you Heart Zheng

---

### Post by Ashtray on 2008-08-03
Great news, thank you.

---

### Post by deep64blue on 2008-08-03
Great stuff - well done!

---

### Post by quitte on 2008-08-03
Thank you Foxconn!
This whole incident will have a huge impact on my future buying decisions and recommendations.
Now If you started contributing to coreboot, even if it wasn't officially supported you would make it an instant buying decision.
I also want to apologise for actually believing you might have broken Linux deliberetely for some time. Good thing mjg gave us an alternative view on this bug.

---

### Post by MisterArcturus on 2008-08-03
It seems that after changing to the Optimized Defaults, you may wish to set your CPU and case fans to automatic, so that the motherboard can dynamically control the speed.

Also set Plug & Play OS to Yes so that the BIOS can't possibly trip up your plug and play device configuration.

---

### Post by MisterArcturus on 2008-08-03
I should also add, it appears that they're doing some more sanity checking about how they're bringing devices out of suspend and where they are and what is happening in the reboot and shutdown stages.

Windows users should even be happy about this, as it would be theoretically possible for a situation to occur in which they experienced data loss, or had to do a hard reset, which of course does not unmount the filesystem, potentially causing considerable damage.

I'm thinking more along the lines of bugs that were just more obvious on non-Windows systems, they should have never shipped this, but they did, and they fixed it now, yay!

---

### Post by gnomey on 2008-08-03
Wow that was fast, usually hardware vendors dont pay attention to the Linux community.

You should now put another sticker on the MoBo's box saying "Linux Compatible" :)

---

### Post by el_pepo on 2008-08-03
Which motherboards are compatible with this BIOS? I have a Foxconn 975X7AB and I have some serious issues (freezes, Linux failing to boot, etc.) when ACPI is active.

I am forced to use boot options "acpi=off noacpi noapic" to make my system usable.

Will this BIOS fix my motherboard? If not, are you going to workaround this issue?

Thanks.

---

### Post by MisterArcturus on 2008-08-03
> **el_pepo said:**
> Which motherboards are compatible with this BIOS? I have a Foxconn 975X7AB and I have some serious issues (freezes, Linux failing to boot, etc.) when ACPI is active.

I am forced to use boot options "acpi=off noacpi noapic" to make my system usable.

Will this BIOS fix my motherboard? If not, are you going to workaround this issue?

Thanks.

I think just the G33M and G33M-S.

Heart left the link to the support system there.

---

### Post by MisterArcturus on 2008-08-03
> **MisterArcturus said:**
> [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

FreeDOS boot CD

Also, I saw an interesting option in the BIOS that lets you use your card reader or a USB thumbstick to emulate a bootable floppy disk drive, so preparing the floppy image as in this example and putting it on a card/thumbgdrive and setting the BIOS to boot from that may also work?

No promises though, Boot CD would be safer.

---

### Post by powerofslack on 2008-08-03
Thanks a million for your timely response to this issue.  Specifically because of this response, I'll always be sure to take a look at Foxconn motherboards when building and upgrading systems, because there's no substitute for responsive support like this.

Thanks again.

---

### Post by ADINSX on 2008-08-03
I was actually holding back on buying a new foxconn mobo because of this issue, but now I think I'll go ahead and add it to my newegg cart.

Thank you foxconn.

---

### Post by ARhere on 2008-08-03
WOW!

I honestly was expecting the typical, "*This Motherboard was not tested with Linux and therefore is not supported.  Sorry for all your troubles.*" response you typically get from companies/vendors.  I am truly impressed!

I will seriously consider FOXCONN for my next computer lab I set up.

-AR

***EDIT: Why in the world are most posters on this thread with a "First Cup of Ubuntu" tag?  Is there something I am missing or is the evil [color=red]Moderator of Doom[/color] back at changing peoples Avatars and ranks again?***

---

### Post by hrvooje on 2008-08-03
It seems that community matters .. hooah  :guitar:

---

### Post by t2000kw on 2008-08-03
I am impressed with the quick response from the company. I wonder if the tech support person who said they don't support Linux and basically told someone to forget trying to get help will be "retrained" or allowed to go and "pursue other business opportunities" outside of the company?

---

### Post by hyapadi on 2008-08-04
A happy ending story. Like it so much!

Keep it up FoxConn!!

---

### Post by Excessive on 2008-08-04
Dear FoxConn,

Thank you very much for your dedication to solve this matter. Most of us are working with IT companies, we redirect people to buy correct computer equipment, and we can show our gratitude with buying Foxconn products from now on.

At least, this is what I will do.

Thank you again for your fast response.

---

### Post by mjbarks on 2008-08-04
Well done Foxconn. Great to see a company listen to and **act** on the requests of its customers.

---

### Post by Infern_o on 2008-08-04
> **serrs said:**
> I think this is great of Foxconn!  Kudos, I will try to buy your MB in the future.

I have a Foxconn P9657AB-8EKRS2H.  It's an older chipset but has (2) PCI-E x16.  I've built a multiseat box for my family around this board.

Problem!  Due to incorrect IRQ routing I *MUST* turn off USB-2.0 or I can potentially pass "irq polling" as a kernel arg.  If I don't the IDE/SATA lockup.

Otherwise it's about the highest quality MB I've come across.  Is there any hope for nasty IRQ routing issues?  (It took me about 16 hours to finally find the above workaround)

Thanks,
Scott
I have the same problem with this motherboard. Even made a kernel bug for this:
[http://bugzilla.kernel.org/show_bug.cgi?id=10572](http://bugzilla.kernel.org/show_bug.cgi?id=10572)

---

### Post by AK Dave on 2008-08-04
I'm pleased with the community response, and pleased that the manufacturer stepped up, but I don't congratulate them for doing so. It was just good business sense. After this all got slashdotted, the hue-and-cry of community "outrage" against Foxconn must have been outrageous. I'm sure I'm not the only person who took time out of his paid day-job to abuse company resources by sending "polite" nastygrams to Foxconn under the guise of "problem reports". Replace "company" with "government" in the above statement.

I applaud the community for stepping up. I am pleased that Foxconn has good business sense enough to enact some rapid damage control. I still won't be eager to buy a Foxconn board until they've actually FIXED the problem: production-grade BIOS release, new board released with new un-flawed BIOS, and a permenant end to the "Linux isn't supported" claims.

---

### Post by Swagman on 2008-08-06
[img]http://farm3.static.flickr.com/2017/1616146653_b1963ca5c4_o.gif[/img]

Foxxconn still deserve kudos for dealing with it quickly.

---

### Post by jay019 on 2008-08-06
> **AK Dave said:**
> I'm pleased with the community response, and pleased that the manufacturer stepped up, but I don't congratulate them for doing so. It was just good business sense. After this all got slashdotted, the hue-and-cry of community "outrage" against Foxconn must have been outrageous. I'm sure I'm not the only person who took time out of his paid day-job to abuse company resources by sending "polite" nastygrams to Foxconn under the guise of "problem reports". Replace "company" with "government" in the above statement.

I applaud the community for stepping up. I am pleased that Foxconn has good business sense enough to enact some rapid damage control. I still won't be eager to buy a Foxconn board until they've actually FIXED the problem: production-grade BIOS release, new board released with new un-flawed BIOS, and a permenant end to the "Linux isn't supported" claims.

I can see where you are coming from. Its one thing to fix something once you are busted and it goes public but to get it right from the beginning is really where its at. Which is why I am happy with my recent purchase of an ASUS motherboard.

---

### Post by mjg59 on 2008-08-06
All reported issues are fixed in current Linux git, with the exception of the reboot after resume issue. I've just sent a (trivial) fix for that to the Linux ACPI list, so it should land in 2.6.27. It should also apply to any earlier kernel versions ([http://www.codon.org.uk/~mjg59/tmp/foxconn.diff](http://www.codon.org.uk/~mjg59/tmp/foxconn.diff)). If people are still having problems, please feel free to let me know.

---

### Post by MButterman on 2009-08-26
Thanks for the quick response. I have a A7GM-S 2.0 with 872F1P03 bios dated 06/23/09. Has a debug bios issued for this model and how do I obtain it. 
 
Mbutterman

---

### Post by MButterman on 2009-09-14
How to ask a question in the Ubuntu Forums? Go elsewhere and find your own answers. Could someone at least give me the correct address of the spirit of ubuntu, obviously he doesn't live here and I would really like to keep in touch with him.

---

### Post by Rocket2DMn on 2009-09-14
MButterman, you are posting in an old thread about a different board - please start a new thread for your problem.  Thank you, and good luck.

---

