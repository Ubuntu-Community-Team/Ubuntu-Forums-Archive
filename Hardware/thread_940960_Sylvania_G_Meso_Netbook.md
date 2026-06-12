---
title: "Sylvania G Meso Netbook"
date: 2008-10-07
forum: Hardware
---

### Post by judahsmith on 2008-10-07
I wanted to start a thread about the new **Sylvania G Meso Netbook** with the **Ubuntu Netbook remix** (pre installed).  I have already heard of a few bugs/issues with the item.  That I wanted to share with others.  Mine will be arriving at my home in the next day or 2.  But here's is an email reply I received from one of my NEW friends at Canonical.  With regard to the web cam issue some have been struggling with.
Here is the contents of that email:

Hi Judah,

I believe a reason your unit was on backorder was due to this BIOS fix (I heard) was being done for the web cam. I would also run the updater in Ubuntu when you get it as there was a fairly large update we added to UNR 1.0 a two weeks ago. If you have a problem out of the box, please call the Sylvania support line as they can help you as well.

Regards,

****

Smith, Judah L. (WSTF-RA)[JTI] wrote:
>
> Who would I contact for user support? I have some concerns about an > issue mentioned by two users who just received their Meso. Mine was on backorder...so I should receive it tomorrow. *It seems from both the items mentioned below the webcam does not work with the software included. *Is this a known issue? My assumption in buying the meso was to have a great "out of the box" experience. Where at least I would know the software included would seamlessly work with the hardware. Is there a need for concern?

[https://answers.launchpad.net/launchpad/+question/47327](https://answers.launchpad.net/launchpad/+question/47327)
Webcam Ubuntu Netbook Remix Sylvania MESO I recently purchased Syvania Netbook MESO run by Ubuntu Netbook Remix. I am unable to open the built-in webcam. I clicked Fn+Esc per Sylvania instruction.  It does not work.  I go to Favorite>Cheese and "Webcam is not recognized" is shown.  I attempted many a way, but webcam is dead.  Can anyone help me please?
Isao Higashide 10/6/08

[http://forum.eeeuser.com/viewtopic.php?id=45610](http://forum.eeeuser.com/viewtopic.php?id=45610)
-The webcam doesn't work with "cheese", the enclosed webcam program. I'm not that surprised--my USB webcam on my desktop doesn't work with cheese, either. I would just download another webcam program (camorama), but . . . -I can't get wired ethernet to work. I don't have a router at home, and have been home-bound today with a bad cold, so I couldn't really try out wireless (one neighbor apparently has an unlocked network, but it was slow as snot, and kept dropping). I figured this wouldn't be a  big deal since the computer has an ethernet port. But I couldn't get it to recognize my ethernet at all on the program that came with it. I ultimately ended up uninstalling the network manager, and installing  <a href="http://wicd.sourceforge.net/">WICD</A>. I can get WICD to "see" my connected internet, but for some reason I still can't use any internet related programs. Arrrg? If I weren't an experienced Linux user (and hadn't been through this sort of thing before), I'd be going out of my mind. As it is, I'll have to continue searching forums for a solution, I guess.

Phoebe

---

### Post by jetpeach on 2008-10-07
I just bought this netbook last week - a few questions:
WEBCAM - how can I fix this? I have the same error mentioned in the launchpad thread linked previously ([https://answers.launchpad.net/launchpad/+question/47327](https://answers.launchpad.net/launchpad/+question/47327)). If there is a bios update, can somebody link?

FAN SPEED/NOISE - See my thread here for details
[http://ubuntuforums.org/showthread.php?t=934942](http://ubuntuforums.org/showthread.php?t=934942)
Summary is I'd like to know how to control the fan speed myself and am willing to take the small risk of crash/overheat. We bought this for notetaking for my girlfriends law school classes, and it needs to be quieter...

WIFI - She is having some issues with super slow connectivity sometimes, even when it says she has 5 bars and her other laptop works fine. More on this to come, but if people also have issues/solutions I'll update here.

REPOSITORIES - Are people sticking with the repositories giving as the defaults in the preinstalled version? These are from Sylvania (EDIT: I didn't read carefully, it does come with Ubuntu/Canonical repositories) and I immediately noticed firefox is out of date and checking these repos for updates didn't find an update for it. Maybe I should switch to my standard ubuntu repo list that I use, but I thought _maybe_ there is some benefit to use the sylvania tailored repos (since afterall, they are for this device)? Is everything for ubuntu-netbook-remix in the regular repositories though? If so, I'd rather just use them since that eliminates the potential of out-of-date programs like firefox is in the sylvania repositories right now.
Update Oct8: In hopes of better updated programs, I tried changing the repositories to the normal ubuntu repositories for hardy, but it won't find them, giving Failed to fetch 404 Not Found errors for all the packages. I can't find out why, as the internet works and the sources.list file works just find on my other computer here. Therefore, I'm using the repositories that came with it, but would like to upgrade Firefox to 3.0.3 so if anybody knows why/when this newer Firefox will be in the remix repositories or how to upgrade it or is able to get the regular ubuntu repos to work, let me know.

So far those are my issues/questions. I think the potential of this to be a great netbook with ubuntu is high, but right now I'm not entirely impressed with sylvania (considering the webcam failed to work right out of the box, and firefox is out-of-date in their repos.)

jetpeach

---

### Post by judahsmith on 2008-10-09
Hi there,
Am I the only one that got a Ubuntu version Meso with windows hardware drivers on the included CD?  How worthless is that.  I mean if I plan to load XP on this machine that's great.  But I purchased this specifically to have a machine pre-installed with ubuntu.  Which means I expected my restore disk, to be a copy of the ubuntu OS with all the unique drivers included, so if I have problems, I can just wipe out the hard drive and reload the OS.  There is an .ISO on their website, but its for Gos. (its a "lame" version of Ubuntu)  But I like the remix version I have.  And I think its only normal business practice, to include a CD that lets you wipe the machine and restore the OS to its original state.  Mac/Windows have been doing it for years.  I love Ubuntu, I am just surprised at this oversight.  Does anyone know if it will be fixed soon, with an .iso that can be downloaded?

---

### Post by judahsmith on 2008-10-09
I am assuming my images from the webcam should look better than this.  :)  But for some reason they are incredibly blurry.  I apparently have the new bios, because the cam works.  But look at the images it puts out.  Its doesn't matter how I turn it or what light I am in.  All the pictures are this bad.  Help?  I have been trying to call Sylvania for some answers....or to let them know some of issues so they can get on them for the next software release.  All I get is voice mails.  :(  Bummer

---

### Post by judahsmith on 2008-10-09
Well I heard from Sylvania today.  There is no restore CD/DVD, but if you fry your installation and want to restore back to the default load.  The hard drive has an extra hidden partition.  To access this partition, simply hold down the ESC key when you start the netbook from a cold boot.  You will see the grub menu, and an option for recovery.

---

### Post by judahsmith on 2008-10-10
I tried everything.  Than I tried the simpliest fix.  I gently sqeezed the plastic right around the webcam lens on my meso, and it slowly came into focus.  I guess the little lens in there got shaken slightly loose during shipping.  Now the cam is crystal clear!  Strange that would happen because the meso actually seems very well made.  Has a nice solidly built feel.  Anyway, its been great ever sence!  So far I'm actually loving my first Ubuntu pre-installed computer.

---

### Post by jetpeach on 2008-10-10
Congratulations on your first Ubuntu pre-install! I still haven't dinked around getting my webcam to work yet, I guess I should email Sylvania about the bios update, hopefully that will fix it.

My box didn't come with any CDs whatsoever! Good to know about holding down the escape key and accessing the hidden partition, I thought the ISO on their site was the ubuntu-netbook-remix, so good to know its gOS...

Let me know if you have any wifi connection issues - I have very strange things happening, but I am thinking I will just wait until Intrepid comes out at the end of the month, upgrade and see if it fixes them.

---

### Post by fixitchris on 2008-10-10
Thanks for starting this thread.

I am going to wait a bit to get my meso, but I do have some questions:

1. [http://sylvaniacomputers.com/products.php?p=meso](http://sylvaniacomputers.com/products.php?p=meso) states that the black laptop comes with 512MB, but on amazon.com I see that the black one comes with 1GB.  Which one is correct?

2. How much is the optional DVD drive?  how much is the case?

3. Has anyone tried installing a different distro of Ubuntu?  How about Debian?

4. Has anyone tried XP yet?  Do the drivers work?

5. What USB devices have you tried so far?

[B]
6. And my final question... Should I just wait for MAGNI???[/B]
([http://blog.laptopmag.com/sylvania-g-netbook-magni-rebranded-msi-wind-coming-for-holidays](http://blog.laptopmag.com/sylvania-g-netbook-magni-rebranded-msi-wind-coming-for-holidays))
aka... Wind U120 ([http://global.msi.com.tw/index.php?func=proddesc&prod_no=1474&maincat_no=135](http://global.msi.com.tw/index.php?func=proddesc&prod_no=1474&maincat_no=135))

Thanks

---

### Post by judahsmith on 2008-10-11
I answered your questions in the quote.  I'm at a coffee shop working on my meso as we speak!  Love it!

> **fixitchris said:**
> Thanks for starting this thread.

I am going to wait a bit to get my meso, but I do have some questions:

1. [http://sylvaniacomputers.com/products.php?p=meso](http://sylvaniacomputers.com/products.php?p=meso) states that the black laptop comes with 512MB, but on amazon.com I see that the black one comes with 1GB.  Which one is correct?

In answer to this question, I got my white meso on Amazon (best price with free shipping at the time) and yes it comes with 1 gig memory.  Which on ubuntu...smokes!  Very fast.

2. How much is the optional DVD drive?  how much is the case?

I don't believe the offical on is out yet.  But I have used two different usb cd/dvd rom burners and the machine recognized them perfectly.

3. Has anyone tried installing a different distro of Ubuntu?  How about Debian?

I love the tweaked version of ubuntu they included so I didn't try any others.

4. Has anyone tried XP yet?  Do the drivers work?

I have.  Drivers work.

5. What USB devices have you tried so far?
2 different usb cd/dvd burners, 1 fugi digital camera, 2 different HP usb printers, bunch of usb sticks,  and a 750 usb external harddrive.  Worked with all of them plug and play.  Oh and two external usb wifi cards just for fun.
[B]
6. And my final question... Should I just wait for MAGNI???[/B]
([http://blog.laptopmag.com/sylvania-g-netbook-magni-rebranded-msi-wind-coming-for-holidays](http://blog.laptopmag.com/sylvania-g-netbook-magni-rebranded-msi-wind-coming-for-holidays))
aka... Wind U120 ([http://global.msi.com.tw/index.php?func=proddesc&prod_no=1474&maincat_no=135](http://global.msi.com.tw/index.php?func=proddesc&prod_no=1474&maincat_no=135))

Thanks

---

### Post by jetpeach on 2008-10-11
judahsmith - i'm curious, how often is the fan speed on your meso on "high" during 'normal' usage (web browsing...)?

---

### Post by judahsmith on 2008-10-14
Mine isn't hardly ever on high.  Runs extremely quiet!  Of course I also loaded Ubuntu Tweak, and set the CPU to max performance when on AC power, and max power savings when on battery.  But even before that I never noticed the fan coming on high.  In the week I have had it, it hit high once or twice for a few seconds at most.  I was surfing all day yesterday and never noticed it on high fan speed.

---

### Post by judahsmith on 2008-10-14
I was at a local coffee shop this weekend.  And was having some coffee a little hummus and cruising the web on my new meso.  And I had three people approach me over the course of 3 hours, asking where I got my "laptop".  One woman said it was the cutest things she had ever seen.  Two guys came over and we amazed at the size, and looks.  Very MACish (I have the snow white version)  (And just to put it to rest....no one thought it was a DVD player.  A few reviews said that about it, but everyone I talked to loved the shape and style.  I showed each person the new gui (Netbook remix) and they loved it.  So easy, so much faster than Vista.  I was telling them how much I love using Ubuntu for the web...no spam, spyware, or viruses.  two of them asked where I got it.  (amazon.com)  I don't know, I think if this little guy was advertised more, and a few issues resolved, it would be a real winner both for Sylvania, and Ubuntu.

---

### Post by judahsmith on 2008-10-14
I just got off the phone with tech support, and I have the bios update file to fix those meso netbooks that can't get the webcam to work.  

Here is the file
[ATTACH]88337[/ATTACH]

And here is the screenshots sent to me of how to run it.
[ATTACH]88338[/ATTACH]

[ATTACH]88339[/ATTACH]

[ATTACH]88340[/ATTACH]

[ATTACH]88341[/ATTACH]

Hope this helps those that have that problem!  

Judah

---

### Post by jetpeach on 2008-10-14
oh sweet, thanks judah that's great. i'll try that fix tonight!

i wonder if the firmware does anything with the fan too - i got ours from compusa and as i said, the webcam didn't work out-of-the-box, but i wonder if it also affects the fan. our meso starts out quiet for about 5 minutes, but then the fan ramps up and stays constant at a pretty loud volume after that. i'll test ubuntu tweak tonight as well as the firmware update, maybe that will help too (although i tried powernowd and a few other tweaks already-even when i lock the cpus to lowest speed at 800 mhz the fan still stays loud.).

thanks again,
jet

---

### Post by PhoebeG on 2008-10-14
Oh, yay, more Sylvania users!

I'm the Phoebe from the Asus forum. I think I was probably one of the first people with the adorable little G. Glad to find other users--and glad you guys have gotten a webcam fix. I've had mine for--about a month now? Here's what I've found:
[LIST]
[*]It's super adorable looking. I brought it out during a graduate English class and all the scholars pretty much gushed at it--"Aw!" I've got the yellow model. Very distinctive. Some finger prints on the lid already, but the matte interior is nice.
[*]Internet: I still haven't been able to get wired ethernet to work. If anyone has a fix for this, let me know. Wireless works, but is a bit slow and finicky. I'm able to check my email at coffeeshops, but downloading updates is an arduous task.
[*]Beware! The openoffice.org installed does not have spell check.
[*]Mine runs superquiet. I'm not sure what these fan complaints are all about. It gets a bit warm to the touch if the side vent is blocked.
[/LIST]

That's all I can think of for now. I got it because I wanted to be able to write in bed, and now, awesomely, I can. While the computing experience hasn't been perfect, I expected that from a just-released Linux model. For the price, I'm more than satisfied.

---

### Post by judahsmith on 2008-10-15
The bios update is now on sylvania's website.  They claim only 200 of the earliest models have the issue with the webcam.  Mine didn't.  It was blurry at first but that was another issue.  Which I resolved.  Also if you change the bios setting from their default optimal settings, the webcam my disappear from Ubuntu.  
My wired network worked perfectly (plug and play), my wireless is super fast, I was working online at a local coffee shop this weekend for about 4 hours and it was doing updates and surfing super fast!  My fan hardly ever runs, and when it does it is for a few brief seconds.  But its is so rare, and quiet, I don't even notice it.  You might call Sylvania and see if their is a patch for that.  They seem extremely helpful!

This was the lady I contacted for customer support, and she was quiet helpful.

Christy Mejia

RCS Professional Services

575 Madison Ave

New York, NY 10022

T: 212-532-9111x1315

F: 212-532-9551

E-mail: [email]cmejia@rcsprofessional.com[/email]  

Two issues I am still having, and she claims they are not issues but they are for me.  When I close my MESO to put it to sleep, it will fall asleep the first time I close it.  But when I open it and wake it up, then try to put it to sleep again, by closing the lid.  It won't fall asleep.  Basically it will only automatically fall asleep the first time I close it.  Then (unless I reboot) I have to put it to sleep with the quit button, but not with the lid.

Other issue. My wireless hotkey still does not work.  Christy (Tech Support) claims it is just slow.  It isn't!  The hotkey does not work.  Not a big deal.  But something to be resolved.

That being said, I still love this little machine.  It rocks!  Very fast, cool, and quiet.  I love the look!  I think it looks like a baby MAC.  And Ubuntu is rock solid.  No bloatware, spyware, virus ware, and crappy software you don't need like windows vista.  The machine runs fast on the 1 gb memory, and Intel atom.  It feels like I am working on a regular full power laptop.  I think if Sylvania markets this right, and works closely with Ubuntu to resolve little issues, Ubuntu Remix could become the NETBOOK OS of choice!  I love it.  Oh and the VGA connection out works.  Had it connected to a external LCD monitor.  (plug and play)  was running at a resolution  1280X1024.  Granted at that resolution it was a little slower.  Not much but a little on refreshing the tabs.  But its was hardly noticeable.  And if you drop the resolution down to 1024x768, it runs full speed.

I added a link to the trash can from the many screen, and a few other tweaks, to make it more user friendly for me.  But now it rocks.  I am running wine on it, for a few windowz programs.  And it runs wine SUPER FAST, compared to some other machines I've had ubuntu on.  It seems they have really tweaked this ubuntu version for the chipset.  And my sources are saying they will soon have an .ISO to download on the Sylvania site, so you can have a back up CD of the OS, if your hard drive ever dies, and you can't get to the recovery partition.

Has anyone gotten COMPIZ to work?  I want to know how to get this machine to work with 3d acceleration.  It was a Intel 945 Express graphics card, but what do I need to do to get the 3d effects working?

---

### Post by zarbuntu on 2008-10-15
I just got my Meso a few hours ago, ran updates and installed VLC. Everything is working well, except Wifi is refusing to connect with WPA or WPA2. It sees the AP, but won't connect. Everything else is excellent, looking forward to getting dual-boot XP on this for my son.:)

---

### Post by Albertkinng on 2008-10-18
> **judahsmith said:**
> Well I heard from Sylvania today.  There is no restore CD/DVD, but if you fry your installation and want to restore back to the default load.  The hard drive has an extra hidden partition.  To access this partition, simply hold down the ESC key when you start the netbook from a cold boot.  You will see the grub menu, and an option for recovery.

I'm doing it, I risk everythng and click yes to recovery, I hope everything go normal again.. Please God put my Meso as it was.... I want Ubuntu .... 

Anyway, I bought in Ebay a USB stick with Ubuntu to have it as an emergency boot disk and installer so, I hope it arrives soon and I can be protected always..

Anyone try to install the regular Ubuntu on the Meso netbook? it is ok? or it need to be just the remix version of it?

---

### Post by Albertkinng on 2008-10-18
> **judahsmith said:**
> I just got off the phone with tech support, and I have the bios update file to fix those meso netbooks that can't get the webcam to work.  

Here is the file
[ATTACH]88337[/ATTACH]

And here is the screenshots sent to me of how to run it.
[ATTACH]88338[/ATTACH]

[ATTACH]88339[/ATTACH]

[ATTACH]88340[/ATTACH]

[ATTACH]88341[/ATTACH]

Hope this helps those that have that problem!  

Judah

when I put my password it quits! and it doesn't let me doit again... What do I do now?

---

### Post by judahsmith on 2008-10-20
> **Albertkinng said:**
> I'm doing it, I risk everythng and click yes to recovery, I hope everything go normal again.. Please God put my Meso as it was.... I want Ubuntu .... 

Anyway, I bought in Ebay a USB stick with Ubuntu to have it as an emergency boot disk and installer so, I hope it arrives soon and I can be protected always..

Anyone try to install the regular Ubuntu on the Meso netbook? it is ok? or it need to be just the remix version of it?
 I did a  restore from the restore partition.  It worked PERFECT!  And I do mean perfect.  Was back to being exactly as it was when I took it out of the box.  However in reference to a Ubuntu usb stick.  Wait for Sylvania to releave the .iso.  The meso uses the new LPIA version of ubuntu instead of the standard i386.  The i386 will work, put will not be optimized for yout INtel Atom Processor.  I.e. it will run slower, and not be optimized to use the battery as well.  I would stick with the LPIA optimized version on your meso, untill Ubuntu releases this on their site.

---

### Post by judahsmith on 2008-10-20
I am currently writing this on my new Sylvania G Netbook MESO.  Which I have now owned for a little over two weeks.  This is the Ubuntu Remix edition, but if the desire moved me I could always throw on a copy of windows XP.  For the record the desire will not be happening any time soon.  Let me first explain why I decided on the MESO and then give a brief review of pros and cons this little machine.

	**WHY DID I BUY: ** Over the last few years I have started to use Linux more and more.  I am not a “geek” persay.  And I don't like having to command line everything.  I like a nice grasphical interface to do nearly all my work.  I'm from the windows 95, XP generation.  So I hunted around and tried a few distributions, SUSE, Madriva (which I loved for a while) and then I discover Ubuntu.  Something about Ubuntu just felt right.  Everyone is different.  But for me Ubuntu felt like home.  Is it a perfect replacement for windows....no.  But it does most of what I need.  And after spending some time working with a Vista laptop, I finally decided that my next laptop would be Ubuntu based.  Vista was too bloated.  Even with all the eye candy turned off....it was slowwwww.  I would run Ubuntu on the same laptop and it was quick and responsive even with COMPIZ (eyecandy working overtime)  So  I wanted a laptop with Ubuntu preinstalled and working right out of the box.  But it seemed that of big commercial companies only DELL offers Ubuntu laptops.  They are very nice looking.  But I just wasn't sold.  Then I saw the new crop of netbooks coming out, and I stumbled upon the Ubuntu web page describing the Netbook Remix GUI.  I decided to make the plunge.  So when the first netbook came out with this version of Ubuntu on it, I purchased it.
[B]
	WHY GET UBUNTU REMIX:  [/B]I wanted it, because it had the power of Ubuntu, but with the simplicity of a mac using the remix GUI.  (once you get use to it.  I come from a PC background (windows) and when I first started working on a Mac it took me a few hours to get comfortable.  The remix was as easy as that to adjust to, if not easier.  My wife who is completely computer illiterate, and can crash any machine in about 30 seconds by just looking at it, and she was up and running on this in no time.  (and as a side note:  Has not been able to crash it yet.)

	**TO MESO OR NOT TO MESO: ** Sylvania?  Don't they make light bulbs?  Yeah they do.  I was a bit wary of buy anything from a relatively no name (computer) company.  And truth be told they are simply slapping their brand on a machine from over seas.  But then again who isn't these days.  I purchased the netbook, because I wanted something inexpensive, (around $350) with a decent harddrive (80gb on the meso), that was small and lightweight from carrying around, and good on battery usage.  The meso met all those needs.  It may not be for everyone, but it was perfect for my needs.  And I can say that any issues I have had, their tech support has walked me through, via emails and telephone calls.  The support has been excellent from Sylvania.
[B]
	THE LOOK:[/B]  A number of site have said it looks like a portable dvd player.  That maybe be so, to some people.  But I have had more complements on the look of this device in the last two weeks, than with any other electronic gadget I have ever owned.  I own the white (snow) version.  Looks like a baby Mac.  And people will come up to me and ask “where did you get such a cute little laptop?  I love it.”  I mention that it uses Ubuntu, and the price.  Most have no idea what Ubuntu is, but when they see the interface, they are like “Wow.”  That's so cool looking, and I can't believe its so inexpensive!”  The build quality is excellent as well.  At no time does the meso feel “cheap”.  It well constructed, and has a  lightweight but solid feel.

	**PROs: ** Great battery life.  I was working at a net cafe for nearly four hours wirelessly and still had charge left in my battery.  Not bad at all.  I had it on the highest power saving setting, and the screen dimmed a bit, but still that excellent.  The screen is nice and bright, and easy on the eyes.  I have the 1 gb ram version, and I find the performance to be excellent.  This version of Ubuntu is tweaked to best use the Intel Atom processor's various abilities, and it is fast and responsive.  Boot time from cold start about 30-45 seconds.  But after that you ready to go.  Not like windows.  45 seconds to boot, then wait another 3-5 minutes while all your programs load.  When Ubuntu is up, its up.  30-45 seconds is not bad at all.  From a suspend mode, you up in 5-7 seconds.  So far hibernate does not work.  I hope they get this function working in the near future.  80 gb hard drive, is fast and quiet.  CPU fan is silent.  I mean it is as quiet as a mouse.  I have heard others having issues with it running at a high rate.  These may have been some of the early models first released of the line.  But mine is stone silent.  The restore partition (in case you jack up your ubuntu) works great!  (I have already tried it, it wipes everything and puts it back to how it was when you first opened the box.)  VGA port works great.  I have it connected to a DELL monitor at 1280X1024 resolution.  Plug and play.  I have hooked up a number of usb sticks, mice, keyboards, external harddrives, CD/DVD burner, two HP printers, all worked plug and play.  If you need a small, lightweight, machine, that won't get viruses and crap ware, this is the machine.  Wireless is very fast.  Excellent for web surfing.  The version of office (Openoffice) that comes with Ubuntu worked great with all my MS office docs!  Just wish they had a real MS ACCESS replacement.
[B]
	CONs:[/B]  Can't hibernate yet (out of the box)  Webcam is a bit subpar.  But for $350 I can let that ride.  Its just not the great.  Keyboard is nice, and firm, with a nice solid feel.  But it is very small.  I have small hands and it is small.  I am getting us to it.  But just know it will take some adjustment.  You have to expect that on a device this size.  Its not too bad, but it will take some time to get use to.  Software repositories need to be refreshed with newer software.   Suspend sometimes hangs when you close the lid to the netbook.  What I mean is, it will suspend automatically when you close you netbook, the first time.  But after you wake it back up, if you close the lid again, nothing happens.  So you need to press the power button, and tell it to suspend.  A minor annoyance.  All the hot buttons work, except the one that turns the wireless off and on.  I called tech support and they said it just turns it off slowly.  But on my unit, it has no effect at all no matter how long I hold down the button or how long I wait.  The mouse buttons and touch pad set up are nice, and have a nice feel.  The buttons do make a rather loud clicking sound when you tap them, which is not a problem unless your in a very quiet environment.  But the touch pad is set up for button clicks, and scrolling.  So you can use the silent touch pad instead if you are in a quiet place.  So it is not really a big issue.  Either Sylvania or Ubuntu needs to release a .iso for this Netbook Remix version of Ubuntu.  It great having an additional recovery partition, but if the whole hard drive craps up you will need some form of media to reinstall.  A small side point.  COMPIZ does not work out of the box.  And in fact I have not been able to get it to work on this machine.  I would love and update to be released so I can enjoy the eye candy of COMPIZ.  I know its doable.  I would just like it out of the box.
[B]
	FINAL VERDICT: [/B] This is the best computer buying experience I have had in a long time.  Due in large part to the Ubuntu installation.  It just works.  Its a poor man's MAC if you will indulge me.  I have fallen in love with the new GUI, and I love the speed.  I have a video playing (MP4, with no choppiness, in video or sound.) and I can be surfing the web, and flip over to a WORD document, all without losing a beat.  It never seems to sure from any lag (like my Vista machine)  No need to defrag, no viruses, no spyware, no registry problems.  When I uninstall a program it is gone (all of it)  The machine and OS are rock solid.  They work beautifully together!  I hope this becomes the OS of choice for NETBOOKS in the future.  For me its a Vista killer.  But be aware it is not a gaming machine.  So if your a game, look else where.  This is a web, email, video, music, word processing, spreadsheet, workhorse.  Though it does seem to play a wicked game of chess.  :)

	**RATING:**
	**APPEARANCE: **8.5
	**BUILD QUALITY: **8
	**PERFORMANCE:** 9
	**INTERFACE:** 10
	**WEBCAM:** 2
	**WEB PERFORMANCE: **8
	**OUT OF THE BOX EXPERIENCE:** 8
	**OVERALL: ** 7.5
	
	I would say if your in the market for a netbook, and want to try something different than windows, but can afford a MAC, this is the machine to get!

---

### Post by Albertkinng on 2008-10-20
> **judahsmith said:**
> I did a  restore from the restore partition.  It worked PERFECT!  And I do mean perfect.  Was back to being exactly as it was when I took it out of the box.  However in reference to a Ubuntu usb stick.  Wait for Sylvania to releave the .iso.  The meso uses the new LPIA version of ubuntu instead of the standard i386.  The i386 will work, put will not be optimized for yout INtel Atom Processor.  I.e. it will run slower, and not be optimized to use the battery as well.  I would stick with the LPIA optimized version on your meso, untill Ubuntu releases this on their site.

I did the restore partition, everything went normal, but the webcam still missing when I try to use Cheese app.... when I bought it it worked perfect, now something happen that Ubuntu doesn't recognize it... and I did the restore, complete erase and all... from the hidden partition. I mean the webcam it's not working at all... I need to know what's going on ?

---

### Post by judahsmith on 2008-10-21
> **Albertkinng said:**
> I did the restore partition, everything went normal, but the webcam still missing when I try to use Cheese app.... when I bought it it worked perfect, now something happen that Ubuntu doesn't recognize it... and I did the restore, complete erase and all... from the hidden partition. I mean the webcam it's not working at all... I need to know what's going on ?

You changed you original (optimal) bios settings.  Tsk tsk tsk.  If you have done a complete restore, and the webcam is not recognized in cheese.  Assuming you have the lastest bios (or have patched the older version, which I mentioned perviously)  Then you somehow changed you bios settings.  

When you first start the machine **hit F2**.  
 When you are in the bios menu go to **exit**, and select **LOAD Optimal Defaults**.  Hit **Yes** to confirm.  Then Exit **SAVING** changes.  Your cam should work just fine.

---

### Post by Albertkinng on 2008-10-21
> **judahsmith said:**
> You changed you original (optimal) bios settings.  Tsk tsk tsk.  If you have done a complete restore, and the webcam is not recognized in cheese.  Assuming you have the lastest bios (or have patched the older version, which I mentioned perviously)  Then you somehow changed you bios settings.  

When you first start the machine **hit F2**.  
 When you are in the bios menu go to **exit**, and select **LOAD Optimal Defaults**.  Hit **Yes** to confirm.  Then Exit **SAVING** changes.  Your cam should work just fine.

ok.... 
I did all that and Cheese still don't recognize the internal cam :( 
do I need to restore the Meso again? What are the steps to start from scratch again?

here what I did.
1) start and press the **esc** key
2) select **restore**
3) hit **enter**
4) reboot

I needed to do all over again, set my user info, set the clock, everything... but the cam doesn't work. the I went to the sylvaniacomputers.com page and download the Bios Update and installed using the terminal, then I download the web cam update and it wont let me install it... everytime I open Terminal and I try to put my password Terminal shuts down!...  the You told me about **LOAD Optimal Defaults** and I did it. but it stills not working. everything else work great . just no webcam.  any other tip for get the cam to work? thanx

---

### Post by Albertkinng on 2008-10-22
I Really Need help here. My Webcam doesn't show up.:confused::confused::confused:

---

### Post by jetpeach on 2008-10-22
hmm, you're problem is quite strange albertkinng, since it was working when you first got it. and you've restored the computer with the restore partition? and the bios back to optimized defaults?

have you updated using the update manager? perhaps that will install any cheeze/webcam updates. from here, debugging gets a little harder - we'd probably need to check if the kernel module was being loaded properly, if other applications can recognize the webcam being there, etc... it might be worth giving sylvania a call, sorry i can't be of more use.

jet

---

### Post by Albertkinng on 2008-10-22
> **jetpeach said:**
> hmm, you're problem is quite strange albertkinng, since it was working when you first got it. and you've restored the computer with the restore partition? and the bios back to optimized defaults?

have you updated using the update manager? perhaps that will install any cheeze/webcam updates. from here, debugging gets a little harder - we'd probably need to check if the kernel module was being loaded properly, if other applications can recognize the webcam being there, etc... it might be worth giving sylvania a call, sorry i can't be of more use.

jet

thanx for your fast response. For some reason my webcam wasn't working even if I did all of this procedures... I call Sylvania and they told me that I just need to press the Fn key and Esc at the same time and suddenly my webcam was working again!!!! how they fix it??? I don't know but it surely is working great! so, others with the same problem do this also to see if it works for you!:guitar:

I'm Back with my Ubuntu little demon!!!

[[img]http://img.skitch.com/20081024-ek9u6qa8ggn5861snje8t17n4s.preview.jpg[/img]](http://skitch.com/ddarts/31yg/photo-133)
[Click for full size](http://skitch.com/ddarts/31yg/photo-133) - [color=#A7A7A7]Uploaded with [plasq](http://plasq.com)'s [Skitch](http://skitch.com)[/color]

[[img]http://img.skitch.com/20081024-dn6pr8ui16hct17a3dhe1u3wnw.preview.jpg[/img]](http://skitch.com/ddarts/31be/photo-132-1)
[Click for full size](http://skitch.com/ddarts/31be/photo-132-1) - [color=#A7A7A7]Uploaded with [plasq](http://plasq.com)'s [Skitch](http://skitch.com)[/color]

---

### Post by judahsmith on 2008-10-27
Killer logo on the front.  It looks fierce!  :)

---

### Post by Albertkinng on 2008-10-28
> **judahsmith said:**
> Killer logo on the front.  It looks fierce!  :)

thanx I made it with Illustrator.. it's not original I got it from a shirt I bought I can't remember where, but I love it so much that I ended up doing a sticker for my Meso! BTW I ended up erasing the whole drive and installing the Ubuntu 8.04 original (not the remix) from scratch and I'm loving it! the animations and all are so great that I think, Microsoft and Apple need to pay attention on this little OS....:guitar:

ooh and Compiz does work. check your Machine. ;)

---

### Post by fixitchris on 2008-11-02
I got mine yesterday. Decent piece of equipment.

My plans are to :

1.  Dual boot XP
2.  Get rid of Ubuntu and install straight Debian
    a.  I was under the impression that the Atom N270 is capable of 64bit instructions, however intel.com says IA64 is not supported.  I will find out I guess.
    b.  I wonder what real advantages the LPIA  build has over x86?  Besides the obvious  battery life...
    c.  I need Debian x86 or ia64 to get a wider selection of packages.  I don't want to  build every package i need for lpia.

Oh... I was able to resize the 72g partition to 20g with partmagic usb stick.

---

### Post by donaldb on 2008-11-08
I am thinking about installing windoz xp
not sure how easy it will be but looks the drivers are on Sylvania's site so it might not be too hard

---

### Post by parnote on 2008-11-12
I **just** received this netbook ... and it REALLY ROCKS! The thing really flies and works really well. I purchased this mostly based on what I read here.

I did have a scare, since I applied the updates and Cheese stopped working. But I got it back, using the tips here.

However, I cannot get Camorama working AT ALL. The only thing I get is a message, stating: "Could not connect to video device (/dev/video0). Please check connection."

Any suggestions?

parnote

---

### Post by the3dman on 2008-11-24
You are correct this netbook rocks! I could not get Camorama working either. I got the same error. Other than that this thing works great! One thing I am not able to do, that I would like to do is upgrade to 8.10 but it wont seem to let me.  In software sources under updates I set it to normal releases but it still says no updates available. Any Ideas?

---

### Post by the3dman on 2008-11-26
I just installed the image from the link listed below and some things seem to work even better than the stock image that comes with this netbook. 

Warning: this image will do a fresh install only and reformat your hard drive, so you may want to make a backup of your original recovery partition. I take no responsibility if you mess up your g meso!

[http://oem-images.canonical.com/unr/](http://oem-images.canonical.com/unr/)

Hope this info helps someone.

Still no 8.10 yet :-(

---

### Post by the3dman on 2008-11-26
Here are some videos of OSX installing and running on my meso. I don't recommend this as there is no sound or wifi. But I did it just for kicks. Now I am back to Ubuntu (Much better)

[http://www.youtube.com/watch?v=TAKzdkxiA5k](http://www.youtube.com/watch?v=TAKzdkxiA5k)
[http://www.youtube.com/watch?v=0AT7n_BA1t8](http://www.youtube.com/watch?v=0AT7n_BA1t8)

---

### Post by the3dman on 2008-11-27
Here is an email I got from techincal support with a link to the Restore Image. They told me that this is not the final image, and that the final image will be uploaded to their website hopefully by the end of the month. This image works great though. To install just unzip and put all files on to a usb flash drive and then from a windows computer run makeboot.bat on the usb flash drive, and it will make it bootable. Warning: only run the makeboot file from the usb flash drive. Running from any other drive will mess up your computer.

PS. Sorry about all the separate posts, just trying to post some useful info since there is not much info out there on this netbook yet.

Here is the email I got with the link:

Here is a link of the UNR you can download until the mean time if you need it instantly. You have to download it on to a flash drive and then run the &#8220;makeboot.bat&#8221; file and it should start installing once reboot.

 

Thank You

 

Sincerely,

 

Christy Mejia

Technical Support

Digital Gadgets

Tel:  (888) 571-0866 

Email: [email]dgsupport@digitalgadgets.com[/email]



the latest image that has been updated to UNR 1 is available here:

[http://people.ubuntu.com/~jouston/20081009-sylvania-unr1-image-autousb.zip](http://people.ubuntu.com/~jouston/20081009-sylvania-unr1-image-autousb.zip)

---

### Post by MsBrooks on 2008-12-16
I received my  Sylvania G Meso Netbook last week and I am new to Linux and Ubuntu. My problem is that I mistakenly edited the last two lines of my recovery in grub menu.lst, so now my recovery doesn't work. Was wondering if it would be the same for all meso's and if so could someone post theirs for me? I have not been able to get the wifi working right. It connects to my wireless router but not the internet. Also I cannot usb cd rom to work on it. Any help would be greatly appreciated. 



MB:confused:

---

### Post by the3dman on 2008-12-24
You can try mine I would think it would be the same.

---

### Post by umaremohsin on 2008-12-31
Hi I have had my meso for a month now and I am loving it so far.  

I am looking to see if someone else has delved into what I am going to do soon.

Windows XP on VirtualBox.

Let me know your thoughts on it.  

I also have another problem with wireless WEP/WPA authentication, ubuntu would not authenticate against it.  I have to disable security to let it connect to the network wirelessly.

---

### Post by qkall on 2009-01-07
> **umaremohsin said:**
> 

I also have another problem with wireless WEP/WPA authentication, ubuntu would not authenticate against it.  I have to disable security to let it connect to the network wirelessly.

i suggest installing the network manager from its ppa.. it uses the same one in 8.10 and works significantly better... [https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)

however.. i had compiz working... then switched to u-lite (openbox  is much faster and lighter than even xubuntu and xfce!) .. but i think my video card is no longer installed (i know openbox isn't compatible with compiz... i have some games that stopped working.. ie tux 2).. anyway to check this?

---

### Post by wabster on 2009-01-10
I received my G Meso this past Thursday. Setup went well as I've used Ubuntu versions before on a second desktop. I think the remix interface works very well on the Meso sized screen. I had the fuzzy webcam problem that someone else on this forum mentioned, but discovered there was a round piece of lens protector plastic covering it. Took the plastic off and now I can see a clear photo. Nice. I'm still having some issues connecting a network printer much as I did on 8.04 desktop version. Intrepid 8.10 made life a lot easier with connections. I wish Sylvania would post an upgrade to that version for remix. Also wish they'd post the remix files since I'm thinking about installing an SSD drive I have and would like to reload remix. I tried downloading the zip file mentioned earlier, but after unzipping it seems the files are corrupted. Tried it several times on different computers but no luck.

I've noticed an occasional click sound from what seems to be the hard drive. Anyone else hear this? It clicks about every twenty seconds or so. The drive seems to work fine, but the clicking is somewhat of a concern. I don't need a drive failure especially since I just got the Meso. I want the SSD drive, but that's not going in until I can get the remix files.

Wireless works well for me even at home with WAP, no SSID broadcast and MAC filter enabled. I've also tried it on three different wifi sites in local cafes, etc. All connected successfully with no problems. I do notice that upon booting the Meso it does take a little while for the wifi card to start up and hunt for available wireless sites. I have a Dell business laptop whose wifi radio starts up immediately after loading XP as does a friend's Macbook. The Meso wifi radio seems a little slow on startup.

Overall I'm pleased with the Meso. The keyboard takes a little getting used to, but I'm doing better on it the more I use it. I think if one is interested in a "netbook" they will find the Meso more than acceptable. The price/value is very good. If one is looking for a laptop, they will probably be disappointed in the Meso much as any other netbook. Better netbooks can be had, but they cost almost as much as a standard laptop and use the same Atom processor, RAM, drives,etc as the Meso. I'd recommend the Meso to anyone looking for a suitable netbook that doesn't want to spend a lot of money. And, the Ubuntu Remix works quite well under netbook conditions. Can't imagine using Windows on a screen this small. I think it would take at least a 10" screen for Windows to be acceptable.

Battery life for me with wireless always on but not Bluetooth is about 3 hours 30 minutes. And that is with fairly constant surfing along with some wordprocessor and email activity working at the same time. Not bad for a unit this small and light. I have been running it down completely and fully recharging overnight since I received it to help condition the battery. I've been told that practice initially will maximize capacity and lifespan.

One last issue. A short while after setting up Ubuntu, I received a notice of 166 available updates. I downloaded and installed all without incident. However, since then the Ubuntu bootup screen just before the desktop appears gives seem some strange error message "Fatal: module battery not found". But I've noticed no change with battery life or the desktop indicator. I've Googled the problem and found other Ubuntu users with the same issue but no apparent resoluton at this point. If any other user has found a solution I'd like to hear about it. No big deal, but I don't like anything showing "fatal" when it comes to computers. Reminds me too much of early Windows experiences:confused:.

Good luck to all fellow G Meso owners. Let's keep the forum posts going.

---

### Post by trojnmandan on 2009-01-10
Hi everyone,

Recently got the meso g, and it seems to work fine except for the wifi. It connects to my network and will load about one page before it is unable to load any more. The "active connection information" box says I'm getting 1mb/s but I don't even think it is that. I have tried updating the bios from the file at sylvania's website with no luck. I have also tried the method of shutting off the wireless and then restarting the computer, also with no improvement. Anyone have any ideas?

Thanks everyone.

---

### Post by the3dman on 2009-01-12
> **wabster said:**
> I received my G Meso this past Thursday. Setup went well as I've used Ubuntu versions before on a second desktop. I think the remix interface works very well on the Meso sized screen. I had the fuzzy webcam problem that someone else on this forum mentioned, but discovered there was a round piece of lens protector plastic covering it. Took the plastic off and now I can see a clear photo. Nice. I'm still having some issues connecting a network printer much as I did on 8.04 desktop version. Intrepid 8.10 made life a lot easier with connections. I wish Sylvania would post an upgrade to that version for remix. Also wish they'd post the remix files since I'm thinking about installing an SSD drive I have and would like to reload remix. I tried downloading the zip file mentioned earlier, but after unzipping it seems the files are corrupted. Tried it several times on different computers but no luck.

I've noticed an occasional click sound from what seems to be the hard drive. Anyone else hear this? It clicks about every twenty seconds or so. The drive seems to work fine, but the clicking is somewhat of a concern. I don't need a drive failure especially since I just got the Meso. I want the SSD drive, but that's not going in until I can get the remix files.

Wireless works well for me even at home with WAP, no SSID broadcast and MAC filter enabled. I've also tried it on three different wifi sites in local cafes, etc. All connected successfully with no problems. I do notice that upon booting the Meso it does take a little while for the wifi card to start up and hunt for available wireless sites. I have a Dell business laptop whose wifi radio starts up immediately after loading XP as does a friend's Macbook. The Meso wifi radio seems a little slow on startup.

Overall I'm pleased with the Meso. The keyboard takes a little getting used to, but I'm doing better on it the more I use it. I think if one is interested in a "netbook" they will find the Meso more than acceptable. The price/value is very good. If one is looking for a laptop, they will probably be disappointed in the Meso much as any other netbook. Better netbooks can be had, but they cost almost as much as a standard laptop and use the same Atom processor, RAM, drives,etc as the Meso. I'd recommend the Meso to anyone looking for a suitable netbook that doesn't want to spend a lot of money. And, the Ubuntu Remix works quite well under netbook conditions. Can't imagine using Windows on a screen this small. I think it would take at least a 10" screen for Windows to be acceptable.

Battery life for me with wireless always on but not Bluetooth is about 3 hours 30 minutes. And that is with fairly constant surfing along with some wordprocessor and email activity working at the same time. Not bad for a unit this small and light. I have been running it down completely and fully recharging overnight since I received it to help condition the battery. I've been told that practice initially will maximize capacity and lifespan.

One last issue. A short while after setting up Ubuntu, I received a notice of 166 available updates. I downloaded and installed all without incident. However, since then the Ubuntu bootup screen just before the desktop appears gives seem some strange error message "Fatal: module battery not found". But I've noticed no change with battery life or the desktop indicator. I've Googled the problem and found other Ubuntu users with the same issue but no apparent resoluton at this point. If any other user has found a solution I'd like to hear about it. No big deal, but I don't like anything showing "fatal" when it comes to computers. Reminds me too much of early Windows experiences:confused:.

Good luck to all fellow G Meso owners. Let's keep the forum posts going.

I get the module failure also but have not found any issues with it. As far as the hard drive clicks you can set your computer to "Laptop Mode" and that should solve that problem. To do this: Open your terminal application and type: gksudo gedit /etc/default/acpi-support
Then change "ENABLE_LAPTOP_MODE=false" to "ENABLE_LAPTOP_MODE=true" then save, close, and reboot. 

The latest image that has been updated to UNR 1 is available here:
(This is directly from Sylvania and for the meso g only)

[http://people.ubuntu.com/~jouston/20081009-sylvania-unr1-image-autousb.zip](http://people.ubuntu.com/~jouston/20081009-sylvania-unr1-image-autousb.zip)


Instructions: Extract all files from the zip file and put on to a 4gb flash drive. Then plug into a windows computer and run the "makeboot" file on the flash drive. After that just plug into the meso g and reboot. Warning: This will erase your computer and make it stock again.

---

### Post by the3dman on 2009-01-12
> **trojnmandan said:**
> Hi everyone,

Recently got the meso g, and it seems to work fine except for the wifi. It connects to my network and will load about one page before it is unable to load any more. The "active connection information" box says I'm getting 1mb/s but I don't even think it is that. I have tried updating the bios from the file at sylvania's website with no luck. I have also tried the method of shutting off the wireless and then restarting the computer, also with no improvement. Anyone have any ideas?

Thanks everyone.

Have you tried cycling power to your wireless router/modem?

---

### Post by wabster on 2009-01-12
the3dman, thanks for the reply. I'll try your solution for the clicking drive issue when I return home from travel later this week. Any idea why the clicking would occur if not in "Laptop Mode" configuration?

Yesterday I received a reply from Sylvania customer service indicating the Ubuntu Remix files should be available on their site by the end of this month. I'll try the link file download again that you provided in the meantime, but the extract didn't work for me the first attempt. Perhaps the Zip file got corrupted during download.

Thanks again for your reply and suggestions.

---

### Post by trojnmandan on 2009-01-12
The3dman, Yes I tried cycling the power to both the router and the cable modem, neither resolved the problem. Any other ideas?

Thanks

---

### Post by the3dman on 2009-01-15
> **wabster said:**
> the3dman, thanks for the reply. I'll try your solution for the clicking drive issue when I return home from travel later this week. Any idea why the clicking would occur if not in "Laptop Mode" configuration?

Yesterday I received a reply from Sylvania customer service indicating the Ubuntu Remix files should be available on their site by the end of this month. I'll try the link file download again that you provided in the meantime, but the extract didn't work for me the first attempt. Perhaps the Zip file got corrupted during download.

Thanks again for your reply and suggestions.

I think the clicks have something to do with the load cycles on the hard drive, and when in laptop mode I guess it lowers the amount of times that the computer spins-up and spins-down the hard drive. If you go to this page it has more information than I can offer on the topic. [http://ubuntuforums.org/showthread.php?t=994598](http://ubuntuforums.org/showthread.php?t=994598)

Regarding sylvania telling you that an image will be available at the end of the month, that is what they told me last month lol. So I hope it does come this month finally.

Hope this Helps

---

### Post by the3dman on 2009-01-15
> **trojnmandan said:**
> The3dman, Yes I tried cycling the power to both the router and the cable modem, neither resolved the problem. Any other ideas?

Thanks

Unfortunately, I don't have many more ideas on this since I have not been able to recreate the issue with my g meso. Have you connected another laptop to the wireless to see if that one works ok? If it does then we know 100% that it is something with the meso g. If you have security on your wireless connection you could also try to unsecure it temporarily to see if this changes anything, or just change the type of security on the router. I have heard of certain types of security that don't work well with ubuntu. If none of this works then I would probably contact customer support it could just be a defect. Their customer support is very good and very quick. The number is on their website at [www.sylvaniacomputers.com](www.sylvaniacomputers.com)

---

### Post by greyfox1 on 2009-01-16
I have the same issue as trojnmandan - the wifi only works sporadically.  It always stays connected but the speed fluctuates between essentially nothing at all and a few kb/s.  More often than not it isn't even usable.  Network Manager says it is connected at 5 mb/s.

When I try to download updates through Update Manager, the indicated download speed is usually listed as "unknown" (this is when it seems not to be working at all).  I have power cycled my modem and router.  Two other laptops running Windows and my desktop running Intrepid have never had issues such as these on the same wireless network.

I'll try disabling security to see if that changes anything.  Other than that I guess I will also be contacting Sylvania support this weekend.

---

### Post by trojnmandan on 2009-01-16
Okay so this is what I have found: I called sylvania tech support and I told them all that I had tried and the only other Idea they had was what the3dman suggested, which is to change the security setting on the wifi. I plan on doing this when I get home today, I'll let you guys know if it helps. I am a little concerned that tech support had no idea. They told me the name of the wifi hardware was rt73usb so I may start looking for alternative drivers. Does anyone have any advice as far as that (alternative drivers) goes? I have looked around launchpad and serial monkey but they most of those issues pertain to rt2500 and rt2x00...


If I can't resolve this soon, I may call the people who sold it to me and ask for a replacement of somekind.

---

### Post by the3dman on 2009-01-16
Here is what I have my routers wireless security set to, and my internet works great.

Security Mode: WEP
WEP Encryption: 64 bits 10 hex digits

I have found that a lot of my devices (Mobile phone, Wii) don't work very well with WPA or WPA2 but since I set to WEP I have had no problems.

I hope this will work for you guys! If you need more help just let me know.

By the way wabster I have posted a guide for the hard drive problem at my site which is more specific to the g meso:
[http://forum.lowpowertech.com/viewtopic.php?f=6&t=5](http://forum.lowpowertech.com/viewtopic.php?f=6&t=5)

---

### Post by greyfox1 on 2009-01-16
I really hope that the problem isn't the security type (I use WPA2).  I wouldn't want to go back to WEP since it's so easily cracked these days.

---

### Post by the3dman on 2009-01-16
I guess I didnt realize that. I guess anything can be cracked these days. Here is something I found since you sparked my interest in this topic.

Here is a quote from this article: [http://www.informit.com/articles/article.aspx?p=369221](http://www.informit.com/articles/article.aspx?p=369221)

"A second flaw exists in the method with which WPA initializes its encryption scheme. Consequently, it's actually easier to crack WPA than it is to crack WEP. This flaw is the subject of this article."


Not sure about WPA2 though, I will keep reading. Edit: It appears that wpa2 can be cracked pretty easy also. Are we ever secure lol? If someone can make it someone can break it.

Although on a side note none of these cracks seem like the average computer user could or would even try using them.

---

### Post by wabster on 2009-01-16
the3dman:

Thanks for the laptop mode tip. I implemented the change in terminal, but the drive still clicks. Strange.

I discovered from your site about finding synaptic. I wondered what happened to it. I loaded smartmontools and checked the drive. Nothing unusual discovered but I'll be checking it periodically to make sure I'm not running into problems.

Appreciate the help!

---

### Post by wabster on 2009-01-16
I'm running WPA with MAC filter and no SSID broadcast on a Linksys WRT600N in G mode with no problems. Meso finds it every time.

I was having wifi problems early on during setup when I received my Meso. I reloaded Ubuntu off the hidden partition after messing something else up and the wifi worked perfectly afterward. Not sure why this fixed it, but it may be worth a try if you haven't done so already.

On another topic, I was having difficulty setting up my networked HP printer. I downloaded the HPLIP Toolbox and it found my HP Officejet Pro L7600 pronto! No muss no fuss. I highly recomnend it for anyone with an HP printer.

---

### Post by the3dman on 2009-01-16
> **wabster said:**
> the3dman:

Thanks for the laptop mode tip. I implemented the change in terminal, but the drive still clicks. Strange.

I discovered from your site about finding synaptic. I wondered what happened to it. I loaded smartmontools and checked the drive. Nothing unusual discovered but I'll be checking it periodically to make sure I'm not running into problems.

Appreciate the help!

Are they quiet fast clicks like when the computer is thinking or are they louder clicks every minute or so? If they are the quicker quieter ones it is probably just that the computer is small and the hard drive is able to be heard better due to the computer being made of thin plastic. Almost all hard drives that are not solid state make clicking sounds if you listen closely this is normal. It is the louder ones that should not be happening as often (This is what the laptop_mode fixes).

---

### Post by wabster on 2009-01-16
It's just light clicks. You're probably right that I'm overly sensitive to the noise due to the size of the case. I'm not going to worry about it but I'll keep an eye on the smartctl report. Thanks for your help.

---

### Post by the3dman on 2009-01-16
> **wabster said:**
> It's just light clicks. You're probably right that I'm overly sensitive to the noise due to the size of the case. I'm not going to worry about it but I'll keep an eye on the smartctl report. Thanks for your help.

Not a problem any time.

---

### Post by trojnmandan on 2009-01-17
Wabster and the3dman,

Can you guys find out what the driver is called that is running your wireless card on your meso g? Thanks =)

---

### Post by the3dman on 2009-01-17
The Driver mine has listed is rt73usb. The wireless is a Realtek RTL8187B.

---

### Post by wabster on 2009-01-18
My driver and wifi card are the same as the3dman's.

---

### Post by trojnmandan on 2009-01-18
Okay, great thanks guys. I'll let the forum know If i can find any solutions, seems like I've exhausted everyone's ideas haha...

---

### Post by the3dman on 2009-01-19
> **trojnmandan said:**
> Okay, great thanks guys. I'll let the forum know If i can find any solutions, seems like I've exhausted everyone's ideas haha...

You could try to change the channel that the wireless broadcasts on. Maybe there is some type of interference. Who knows, maybe worth a shot.

---

### Post by mttnry on 2009-01-19
Heyas everyone,
I ordered my meso g yesterday off amazon and have been surfing around getting excited and reading about it and felt like sending a hey on this thread.  The ETA is Wednesday. Hopefully Thursday I can write down my first impression of this little guy. 

till then,

---

### Post by the3dman on 2009-01-19
> **mttnry said:**
> Heyas everyone,
I ordered my meso g yesterday off amazon and have been surfing around getting excited and reading about it and felt like sending a hey on this thread.  The ETA is Wednesday. Hopefully Thursday I can write down my first impression of this little guy. 

till then,

Well I am glad to hear you decided on the Meso g. I hope you enjoy it as much as I do. If you have any questions just ask either here or at the page in my signature and I will do my best to help.

---

### Post by mttnry on 2009-01-23
Alright I have now had my meso G for a day.  My experience so far has been great.  The webcam worked out of box and skype installed fine after I updated.  After playing around with the netbook remix version of ubuntu I have been able to find my way around. (I had the hardest time finding the synaptic package manager, until I found the main menu app).  The battery life is great but has averaged out to about 3 hours (I recall someone saying that they could get 4 hours I need to figure out how to do that)  I plugged in a bluetooth adapter and have been using a bluetooth mouse because i have always had a hard time using computer touch pads.  my experiences with bluetooth and ubuntu have always been very smooth.  I am really happy with my netbook and with that said here are the cons.

cons:

before I bought the meso g and was looking at reviews they all said that the keyboard was very small.  They all were right.  The keyboard is even smaller than other netbook's keyboards.  That being said I am getting used to it.  With only one day of getting used to the keyboard im at about 65 wpm where I type around 75 on my desktop.  

I have always hated  touchpads and I still do.

glitches:

in my experience uspend and ubuntu have never been the best of friends.  Like others I have noticed that after the first closing of the screen induced suspend closing the screen again will not send the computer to suspend.  Also when I leave the ac adapter put it on suspend and then turn it on with out the ac adapter it still says that its on ac power.  

I bought my netbook for taking notes in class, typing/surfing in bed, using skype on the go and for travel (I live in milwaukee and travel to and back from chicago almost every weekend).  Taking notes has been great, Im typing this in bed right now so that is great.  Skype calls are alright when calling my girlfriend, she said that the audio is fine(using built in microphone) but the video isnt as clear as when im on my windows partition of my desktop.  Maybe this is because the linux version of skype needs to be updated very badly (when making video calls on my ubuntu partition of my desktop she complains about the same thing) because the pictures that I take in cheese are great quality for a webcam.  Ill have to wait till next weekend before I talk about how this guy is on the road.

So overall I would give this netbook a 9 out of 10. I am very happy, but would have liked a little bigger of a keyboard,

for anyone reading this before making the decision to buy one of these, and are curious of the quality of photos from the webcam here is  a picture I took with cheese( I was curious about this before purchasing so if anyone else is as well here you go)  The picture is with the black and white filter but it takes fine colors as well :)
[ATTACH]100785[/ATTACH]

I am having a little difficulty getting to my desktop's windows shared files.  If someone could point me in the right direction that would be great.  (I wanna put some videos on here for the trip next weekend)  thanks

--
matt

---

### Post by the3dman on 2009-01-23
> **mttnry said:**
> Alright I have now had my meso G for a day.  My experience so far has been great.  The webcam worked out of box and skype installed fine after I updated.  After playing around with the netbook remix version of ubuntu I have been able to find my way around. (I had the hardest time finding the synaptic package manager, until I found the main menu app).  The battery life is great but has averaged out to about 3 hours (I recall someone saying that they could get 4 hours I need to figure out how to do that)  I plugged in a bluetooth adapter and have been using a bluetooth mouse because i have always had a hard time using computer touch pads.  my experiences with bluetooth and ubuntu have always been very smooth.  I am really happy with my netbook and with that said here are the cons.

cons:

before I bought the meso g and was looking at reviews they all said that the keyboard was very small.  They all were right.  The keyboard is even smaller than other netbook's keyboards.  That being said I am getting used to it.  With only one day of getting used to the keyboard im at about 65 wpm where I type around 75 on my desktop.  

I have always hated  touchpads and I still do.

glitches:

in my experience uspend and ubuntu have never been the best of friends.  Like others I have noticed that after the first closing of the screen induced suspend closing the screen again will not send the computer to suspend.  Also when I leave the ac adapter put it on suspend and then turn it on with out the ac adapter it still says that its on ac power.  

I bought my netbook for taking notes in class, typing/surfing in bed, using skype on the go and for travel (I live in milwaukee and travel to and back from chicago almost every weekend).  Taking notes has been great, Im typing this in bed right now so that is great.  Skype calls are alright when calling my girlfriend, she said that the audio is fine(using built in microphone) but the video isnt as clear as when im on my windows partition of my desktop.  Maybe this is because the linux version of skype needs to be updated very badly (when making video calls on my ubuntu partition of my desktop she complains about the same thing) because the pictures that I take in cheese are great quality for a webcam.  Ill have to wait till next weekend before I talk about how this guy is on the road.

So overall I would give this netbook a 9 out of 10. I am very happy, but would have liked a little bigger of a keyboard,

for anyone reading this before making the decision to buy one of these, and are curious of the quality of photos from the webcam here is  a picture I took with cheese( I was curious about this before purchasing so if anyone else is as well here you go)  The picture is with the black and white filter but it takes fine colors as well :)
[ATTACH]100785[/ATTACH]

I am having a little difficulty getting to my desktop's windows shared files.  If someone could point me in the right direction that would be great.  (I wanna put some videos on here for the trip next weekend)  thanks

--
matt

Just so you know if you go to [www.sylvaniacomputers.com](www.sylvaniacomputers.com) and go to the support section there is a bios download that will fix the suspend issue.

---

### Post by keeptrying1188 on 2009-01-24
hi everyone,

i've had my G Meso for 3 days and i am really enjoying it. a lot of the glitches mentioned here in this forum have troubled me too but still it is a lot of fun, convenience and i'm also getting used to the scrunched keyboard. i really love the size and weight of this netbook and i use it now all the time when i'm away from my keyboard.

in the 1st couple of days i had to restore (to original) the hard drive because of the wireless connection. now it is working ok (not that great) but it is still quite erratic. any geniuses here who has any idea if one could use a wireless USB stick with the G Meso? If so which make/model...

i  know that there's a backup program somewhere that came with the netbook on UNR but where do i locate it?

help me as i stumble thru this beginner's journey in learning the G Meso and UNR. i will be very grateful n will pass it on in this forum.

i have the snow G Meso.

---

### Post by the3dman on 2009-01-24
> **keeptrying1188 said:**
> hi everyone,

i  know that there's a backup program somewhere that came with the netbook on UNR but where do i locate it?

i have the snow G Meso.

What are you trying to back up? Just all your settings?

---

### Post by keeptrying1188 on 2009-01-24
Yes, everything on the hard drive. Hope there's a program or applet for this task like the MAC OS X or any other.

---

### Post by the3dman on 2009-01-25
> **keeptrying1188 said:**
> Yes, everything on the hard drive. Hope there's a program or applet for this task like the MAC OS X or any other.

I have found that clonezilla works the best for me.

---

### Post by keeptrying1188 on 2009-01-25
Thanks, the3dman, i appreciate that. i'll look for it. i also found something called 'sbackup' suggested by another G Meso owner which i was able to use terminal to extract. If anyone's interested these are the lines to type in Terminal:

sudo apt-get install sbackup

Can you tell me where to find clonezilla?

---

### Post by the3dman on 2009-01-27
[http://clonezilla.org/](http://clonezilla.org/)

Its basically Norton Ghost for linux.

[http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php](http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php)

Download the ZIP file for USB Flash drives, or the ISO if you plan on hooking up an external dvd drive.

---

### Post by slantyeyeddevil on 2009-01-27
I've had the Meso for about a month and overall, I'm pleased with it.

No major problems so far.

My concern is with Ubuntu/Linux. The learning curve seems remarkably steep and finding hardware that "just works" with it appears problematic.

My questions to fellow Meso users: what hardware are you using with your netbook (specifically external dvd drives, monitors, printers and portable mp3 players)? Which brands are you using, what problems did you encounter, and how did you solve them? 

I'm new to Linux and netbooks and any thoughts and pointers are appreciated. Thanks!

---

### Post by wabster on 2009-01-28
slantyeyeddevil:

I've got my g meso assigned to a networked HP Pro 7680 printer. Haven't used any other devices with it except SD and USB drives. The printer gave me a little trouble to install and I ended up downloading the HP Print manager through synaptics. It recognized the networked printer immediately and installed it. SD and USB drives have been no problem. I haven't connected it to a monitor as yet, but I will try and let you know the outcome.

I had previous experience with Ubuntu, so the remix was not an issue for me. Although, in my experience the Ubuntu version 8.10 is much more robust at recognizing and installing devices than 8.04. That's why I wish Sylvania would upgrade the g meso remix to 8.10. I think users would find it much more friendly especially for installing devices and applications.

Overall, I'm pleased with the g meso. I'm using it more often now and actually take it with me instead of my Macbook. The size and weight makes it much easier to carry around. However, for heavier word processing needs, etc, I'm back to the Macbook or my Vista desktop. And, an XP Dell work laptop is used for that purpose. I use the g meso for what it was intended, and for that it does quite well.

---

### Post by rick71 on 2009-01-29
I have had my Meso for about 4 hours. It seems to me there are a lot of apps missing. I can find Add/Remove Software in the menus, but no Synaptic, even though I can start Synaptic from a terminal. I can't find Skype. Take screenshot is missing. There are others.

My Meso is one that has the "always on" loud fan. I am considering DLing and installing the BIOS update from Sylvania. Does anyone know if it might fix the fan problem?

On the plus side, the camera is sharp. Slow, but sharp :-)

Can apps be installed from the Canonical repositories? Will they run slower than ones from Sylvania's repository?

Will tarballs compile properly on the Meso? (configure/make/make install)

How do I get spell checking in OO.o?

In a regular Ubuntu install there is a menu entry for Windows under preferences. That is missing on my Meso. Anyone have any idea how to get it back?

Any help or hints appreciated.

---

### Post by the3dman on 2009-01-29
> **slantyeyeddevil said:**
> I've had the Meso for about a month and overall, I'm pleased with it.

No major problems so far.

My concern is with Ubuntu/Linux. The learning curve seems remarkably steep and finding hardware that "just works" with it appears problematic.

My questions to fellow Meso users: what hardware are you using with your netbook (specifically external dvd drives, monitors, printers and portable mp3 players)? Which brands are you using, what problems did you encounter, and how did you solve them? 

I'm new to Linux and netbooks and any thoughts and pointers are appreciated. Thanks!

----------------------------------------------------

Things I Use:

HP Photosmart D7460 - This printer works great out of the box including the wireless.

Multiple USB Hard Drives - (Western Digital, Maxtor, and Segate all 500gb)

Multiple USB DVDRW Drives - (Sony, Lite-On, and LG)

Kodak Z712IS Digital Camera - Works out of the box.

Sprint USB Mobile Broadband Card (Compass 597) - Took a little setup, but works great.

Ipod Shuffle - Some setup required, but also works great.

T-Mobile Dash - A lot of setup required for this one.

Interlink Bluetooth Mouse  - Works out of the box, but requires a blutooth adaptor.

Cirago Mini Bluetooth adaptor USB - Works out of the box.

------------------------------------------------------------

You are correct that Ubuntu or Linux in general has a learning curve, but once you learn it and take the time to figure it out, It can be your best friend. I grew up using Windows so moving to Linux was very difficult for me just because it wasn't what I  was used to. Now that I have learned how it works and how to use it, I would never go back to windows. It is a way more stable operating system. Also I know this may sound stupid, but I actually enjoy when it is difficult to get something to work right, because I am a problem solver and I learn a lot from figuring things out. Hope this helps.

---

### Post by the3dman on 2009-01-29
> **rick71 said:**
> I have had my Meso for about 4 hours. It seems to me there are a lot of apps missing. I can find Add/Remove Software in the menus, but no Synaptic, even though I can start Synaptic from a terminal. I can't find Skype. Take screenshot is missing. There are others.

My Meso is one that has the "always on" loud fan. I am considering DLing and installing the BIOS update from Sylvania. Does anyone know if it might fix the fan problem?

On the plus side, the camera is sharp. Slow, but sharp :-)

Can apps be installed from the Canonical repositories? Will they run slower than ones from Sylvania's repository?

Will tarballs compile properly on the Meso? (configure/make/make install)

How do I get spell checking in OO.o?

In a regular Ubuntu install there is a menu entry for Windows under preferences. That is missing on my Meso. Anyone have any idea how to get it back?

Any help or hints appreciated.

The Synaptic Package Manager is not enabled by default, here are instructions on how to enable it.
[http://forum.lowpowertech.com/viewtopic.php?f=6&t=6](http://forum.lowpowertech.com/viewtopic.php?f=6&t=6)

----------------------------

Skype does not come installed, you must download it from their website.

----------------------------

Definitely Install the Bios update it actually solves a few issues.

----------------------------

Not sure about spell check, but I will look into it.

---

### Post by rick71 on 2009-01-30
----------------------------
"Skype does not come installed, you must download it from their website."


I will take a look. I have heard mention that software not compiled/configured for the Atom runs slower. Might this be a problem with software installed from non-repository sites?

----------------------------
"Definitely Install the Bios update it actually solves a few issues."

"
I used my  meso a little while this morning, on battery. The fan did not come on. I wonder if it is a power management thing. At any rate I have DLed the BIOS update.

----------------------------
"Not sure about spell check, but I will look into it."

Thanks. I guess if you can install Skype from Skype's web site you can do the same with OO.o, but I'd rather use "officical packages."

Thanks for the help.

---

### Post by the3dman on 2009-01-30
> **rick71 said:**
> ----------------------------
"Skype does not come installed, you must download it from their website."


I will take a look. I have heard mention that software not compiled/configured for the Atom runs slower. Might this be a problem with software installed from non-repository sites?

----------------------------
"Definitely Install the Bios update it actually solves a few issues."

"
I used my  meso a little while this morning, on battery. The fan did not come on. I wonder if it is a power management thing. At any rate I have DLed the BIOS update.

----------------------------
"Not sure about spell check, but I will look into it."

Thanks. I guess if you can install Skype from Skype's web site you can do the same with OO.o, but I'd rather use "officical packages."

Thanks for the help.

You can convert all i386 deb files to lpia deb files with this script. This works great for skype. Here is how:

1.) Put the script file in the folder with your deb files.... *_i386.deb

2.) right click on the downloaded deb2lpa_en.sh and goto properties

3.) Click on Permissions Check the box to the right of Execute

4.) Now double click on the deb2lpa file and choose either "run in terminal" or just "run".

5.) You should see new deb files in the format *_lpia.deb as well as your old i386.deb files.

6.) goto command prompt and cd into the Deb files folder. use the following command
sudo dpkg --install *lpia.deb

---

### Post by the3dman on 2009-01-30
I did check and my OpenOffice has spell check and is working great. If yours doesn't maybe just try updating to 3.0

---

### Post by qkall on 2009-01-30
hey i've been wondering this for sometime... i installed xubuntu 8.04 as soon as i got my meso... i just really didn't like remix... but now i'm a bit curious how much better the lpia kernel would work.. how do i go about installing this kernel? i couldn't find it in the repo... maybe mine are incomplete.

---

### Post by rick71 on 2009-01-30
I don't see Open Office in the regular repositories.

I also tried to update the BIOS.  The update failed. 

I got the following error:
****************************************

root@rick:~/Downloads/BIOS update/R18_Linux# ./update.sh
insmod: error inserting 'isfl_drv.ko': -1 Invalid module format
LC89R018.SVN
/all
/dc






Error: Can't open device file isfl
root@rick:~/Downloads/BIOS update/R18_Linux# 

*********************************************
Any  ideas?

---

### Post by the3dman on 2009-01-30
> **rick71 said:**
> I don't see Open Office in the regular repositories.

I also tried to update the BIOS.  The update failed. 

I got the following error:
****************************************

root@rick:~/Downloads/BIOS update/R18_Linux# ./update.sh
insmod: error inserting 'isfl_drv.ko': -1 Invalid module format
LC89R018.SVN
/all
/dc


Error: Can't open device file isfl
root@rick:~/Downloads/BIOS update/R18_Linux# 

*********************************************
Any  ideas?

I had this same problem, and I restored the computer back to factory state, and before installing or updating anything install the bios update and everything worked fine for me. (After you download any updates it stops the bios update from working correctly)


As for open office, Ubuntu has not officially included Open Office 3.0 in the repositories yet because they have not had much time to test it yet, but you can update it manually here is how:

I completely removed all OO related installs through Synaptic.

Downloaded the file (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) from Openoffice.org . You will need to select your language specific download file unless you wish the English version.

Created a directory in /home/name/whatever. EDIT: when extracting the files it will create it's own directories, DEBS and desktop-integration, within another directory with a cryptic looking name. You really only need to extract to /home or whatever you desire.

Extracted files using the default Gnome compression utility to the created directory. Accomplished by double click on the downloaded file.

Went to terminal and "cd" to new directory (example: /home/name/OO3/DEBS) then entered "sudo dpkg -i *.deb" The "DEBS" sub-directory is created when extracting. This installs the program.

Then changed to the other sub-directory created during extract (~/DEBS/desktop-integration) and repeated command "sudo dpkg -i *.deb". This creates the menu choices.

Started OO 3.0 and it works like a charm for me.

---

### Post by the3dman on 2009-01-30
> **qkall said:**
> hey i've been wondering this for sometime... i installed xubuntu 8.04 as soon as i got my meso... i just really didn't like remix... but now i'm a bit curious how much better the lpia kernel would work.. how do i go about installing this kernel? i couldn't find it in the repo... maybe mine are incomplete.

I have found that the lpia kernel does not work that much better. I am running 8.10 and have not found that much of a difference. In fact the only difference I found was that a few (very few) programs do not run well on the small 1024X600 screen with a regular i386 distro. But then again I have found programs that do the same thing in the lpia kernel (such as inkscape)

---

### Post by gandhii on 2009-01-31
Sorry if this already has been mentioned in this thread...  but if not.

So, here is how you remove the ugly sylvania logo on the ume-launcher window. Basically we swap out the png image used with another one that just consists of one pixel that is transparent. You can make your own in gimp or use the one I made at [http://derekparr.com/stuff/blank.png](http://derekparr.com/stuff/blank.png) and put in your home directory.

The file to change is /opt/branding/SYLVANIA.png
Note that the first part of the file name is in caps and that all unix OS's, including Linux, are case sensitive. So type it as you see it.

First, make a backup:
```
sudo cp /opt/branding/SYLVANIA.png /opt/branding/SYLVANIA.png.bak
```

Second, copy blank.png over the ugly logo and make ownership and permissions don't change:
```
sudo cp ~/blank.png /opt/branding/SYLVANIA.png
sudo chown root:root /opt/branding/SYLVANIA.png
sudo chmod 644 /opt/branding/SYLVANIA.png
```

Do a directory listing to make sure everything looks right:
```
ls -la /opt/branding/
```

It should look like this:
```
-rw-r--r-- 1 root root    178 2009-01-30 15:55 SYLVANIA.png
-rw-r--r-- 1 root root 124594 2009-01-30 10:31 SYLVANIA.png.bak
```

Now log out and log back in. The ugly logo should now be gone.

---

### Post by wabster on 2009-01-31
ghandii:

You made it pretty. Nice instructions. You're my hero. Thanks for the post!

---

### Post by rick71 on 2009-01-31
> **the3dman said:**
> I had this same problem, and I restored the computer back to factory state, and before installing or updating anything install the bios update and everything worked fine for me. (After you download any updates it stops the bios update from working correctly)

I don't see anyway to do a system/factory restore. On boot, F2 goes to BIOS, and F12 shows the standard kernel. My "Support CD" is Windows based. How can I go about doing a factory restore? And, when doing a full restore.. does that take it back to the same factory default software install as when I bought it?

Thanks for the help.

---

### Post by rick71 on 2009-01-31
I just seem to keep messing up ...

I have been switching back and forth bewteen Classic view and and  Netbook view.

In the Netbook view I seem to have lost the battery/power indicator and the wireless indicator. They are present in Classic view.

Does anyone know how to get them back?

And... does anyone know how to get windows to NOT open in full screen view in Classic view mode.

I have also found out, if you switch between Classic and Netbook views, any most theme settings set in classic view will be lost. Window Decorations seem to stick.

If I could get the windows to open "normaly" in classic view, I might stay with that view, OTOH, if I could get themes to work in Netbook view, I might stick there.

---

### Post by the3dman on 2009-01-31
> **rick71 said:**
> I don't see anyway to do a system/factory restore. On boot, F2 goes to BIOS, and F12 shows the standard kernel. My "Support CD" is Windows based. How can I go about doing a factory restore? And, when doing a full restore.. does that take it back to the same factory default software install as when I bought it?

Thanks for the help.

To do a system restore, restart the computer and as soon as it restarts hold down the escape key until it goes to the grub menu and then select the menu option that has restore in it, and it will take you through the restore process, and restore it to the day you got it.

---

### Post by the3dman on 2009-01-31
> **rick71 said:**
> I just seem to keep messing up ...

I have been switching back and forth bewteen Classic view and and  Netbook view.

In the Netbook view I seem to have lost the battery/power indicator and the wireless indicator. They are present in Classic view.

Does anyone know how to get them back?

And... does anyone know how to get windows to NOT open in full screen view in Classic view mode.

I have also found out, if you switch between Classic and Netbook views, any most theme settings set in classic view will be lost. Window Decorations seem to stick.

If I could get the windows to open "normaly" in classic view, I might stay with that view, OTOH, if I could get themes to work in Netbook view, I might stick there.

Themes don't work well in netbook mode mostly because it was designed to work specifically with that theme. As for normal mode to remove the auto-maxamize function open terminal and type: sudo apt-get remove maximus

If you remove this the netbook remix function may not work correctly though. This is only supposed to be used if you only use normal mode.

---

### Post by rick71 on 2009-01-31
> **the3dman said:**
> To do a system restore, restart the computer and as soon as it restarts hold down the escape key until it goes to the grub menu and then select the menu option that has restore in it, and it will take you through the restore process, and restore it to the day you got it.

The system restore seems to have worked. The BIOS update seems to have worked. How do I check to see if the BIOS update on the Meso is the new one?

The fan is staying on while the Meso is plugged in. I guess that's a power management setting somewhere. The camera still works.

The first time I tried to resume from shutting the lid, it hung. I did a CTR-alt-del, which restarted the machine. I did a shutdown, then restarted. Resume now seems to work. I just have to find the setting so I don't have to put in my password to unlock the machine.

BTW, your Meso threads in your sig are very help full.

Well, now I know how to fix the machine if I mess things up. Now I just need to figure out how to get the newest recover files on to a USB stick just in case I really bork thing s up.

---

### Post by rick71 on 2009-01-31
> **the3dman said:**
>  As for normal mode to remove the auto-maxamize function open terminal and type: sudo apt-get remove maximus

If I remove Maximus, and the "remix desktop" doesn't work, do think just re-installing Maximus will fix the problems? ... ah, well, I guess I can always restgore :-)

---

### Post by rick71 on 2009-01-31
> **the3dman said:**
> Themes don't work well in netbook mode mostly because it was designed to work specifically with that theme. 

While In Netbook view, I installed the AquaX theme, and changed icons to Industrial. It seems to have worked. Hopefully it will stick through a Suspend/Resume and though reboots.

---

### Post by rick71 on 2009-01-31
My Open Office wouldn't spell check. It does now. Look for this file:

/usr/share/myspell/dicts/DicOOo.sxw. Make sure you can run macros in OpenOffice. Open the file. Select your language and then just follow the directions.

---

### Post by the3dman on 2009-01-31
> **rick71 said:**
> If I remove Maximus, and the "remix desktop" doesn't work, do think just re-installing Maximus will fix the problems? ... ah, well, I guess I can always restgore :-)

Yes that is correct I stated that in my prev. post. 

"If you remove this the netbook remix function may not work correctly though. This is only supposed to be used if you only use normal mode."

---

### Post by rick71 on 2009-01-31
> **qkall said:**
> hey i've been wondering this for sometime... i installed xubuntu 8.04 as soon as i got my meso... i just really didn't like remix... but now i'm a bit curious how much better the lpia kernel would work.. how do i go about installing this kernel? i couldn't find it in the repo... maybe mine are incomplete.

qkall,

You might want to consider restoring Remix, and then using the Classic Ubuntu view. You can switch views form either the Preferences, or administration... I forget which.

---

### Post by rick71 on 2009-01-31
> **gandhii said:**
> Sorry if this already has been mentioned in this thread...  but if not.

So, here is how you remove the ugly sylvania logo on the ume-launcher window. Basically we swap out the png image used with another one that just consists of one pixel that is transparent. You can make your own in gimp or use the one I made at [http://derekparr.com/stuff/blank.png](http://derekparr.com/stuff/blank.png) and put in your home directory.

The file to change is /opt/branding/SYLVANIA.png(snip)

Thanks for an idea. I just edited the Sylvania.png. I filled the white with black. It looks a lot better without removing the Sylvania brand. I suspect it will look better with a "stock" desktop. I have switched to the Industrial icons, and am using the AquaX theme. I switched the GDM theme to Bluetux from Gnome-look. Looks much better, IMHO :-)

---

### Post by the3dman on 2009-02-01
> **rick71 said:**
> 

BTW, your Meso threads in your sig are very help full.



I am glad to hear that, thank you. If you think of things that need to be added to it please let me know also feel free to register and add things yourself if you wish.

---

### Post by gandhii on 2009-02-01
> Thanks for an idea. I just edited the Sylvania.png. I filled the white with black.
You could also just fill in the background with transparent pixels,  The PNG format does support transparency.

---

### Post by gandhii on 2009-02-01
> **rick71 said:**
> If I remove Maximus, and the "remix desktop" doesn't work, do think just re-installing Maximus will fix the problems? ... ah, well, I guess I can always restgore :-)

You should also be able to switch on and off maximus in Preferences/Session.  Then you wouldn't need to worry about having to reinstall from scratch.

---

### Post by rick71 on 2009-02-01
> **gandhii said:**
> You could also just fill in the background with transparent pixels,  The PNG format does support transparency.

I didn't think of filling with transparency. That would allow the underlying desktop image to show through. Thanks again.

---

### Post by wabster on 2009-02-01
> My Open Office wouldn't spell check. It does now. Look for this file:

/usr/share/myspell/dicts/DicOOo.sxw. Make sure you can run macros in OpenOffice. Open the file. Select your language and then just follow the directions.


rick71:

Me now have spellcheck thanks to you. Great post!!

---

### Post by rick71 on 2009-02-01
Great  :-)

I was just passing along info I got from others on the Web.

---

### Post by keeptrying1188 on 2009-02-02
> **the3dman said:**
> I had this same problem, and I restored the computer back to factory state, and before installing or updating anything install the bios update and everything worked fine for me. (After you download any updates it stops the bios update from working correctly)


As for open office, Ubuntu has not officially included Open Office 3.0 in the repositories yet because they have not had much time to test it yet, but you can update it manually here is how:

I completely removed all OO related installs through Synaptic.

Downloaded the file (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) from Openoffice.org . You will need to select your language specific download file unless you wish the English version.

Created a directory in /home/name/whatever. EDIT: when extracting the files it will create it's own directories, DEBS and desktop-integration, within another directory with a cryptic looking name. You really only need to extract to /home or whatever you desire.

Extracted files using the default Gnome compression utility to the created directory. Accomplished by double click on the downloaded file.

Went to terminal and "cd" to new directory (example: /home/name/OO3/DEBS) then entered "sudo dpkg -i *.deb" The "DEBS" sub-directory is created when extracting. This installs the program.

Then changed to the other sub-directory created during extract (~/DEBS/desktop-integration) and repeated command "sudo dpkg -i *.deb". This creates the menu choices.

Started OO 3.0 and it works like a charm for me.
the3dman:

How does one check which BIOS is in our G Meso using the Terminal. Thanks. I'm not sure if i have the latest BIOS.

---

### Post by the3dman on 2009-02-02
> **keeptrying1188 said:**
> the3dman:

How does one check which BIOS is in our G Meso using the Terminal. Thanks. I'm not sure if i have the latest BIOS.

Not sure how to do this in terminal but you can check your bios version by pressing F2 at startup and it will take you into the bios setup and tell you the revision number in the top right corner. The newest is "Rev. 3.5"

---

### Post by keeptrying1188 on 2009-02-02
Thanks so much. I found that the newest BIOS is on my G-Meso. Now i have to figure out whether i updated the BIOS after i updated all the other files, etc. or before as i have the message that tells me: 'Fatal: Module battery not found' at start up. Then when i close the lid to sleep the G-Meso and then open it up again i have a whole slew of error messages hanging and i had to restart it all over again! It is quite a mess and i don't know what to do to clean it up.

---

### Post by the3dman on 2009-02-02
> **keeptrying1188 said:**
> Thanks so much. I found that the newest BIOS is on my G-Meso. Now i have to figure out whether i updated the BIOS after i updated all the other files, etc. or before as i have the message that tells me: 'Fatal: Module battery not found' at start up. Then when i close the lid to sleep the G-Meso and then open it up again i have a whole slew of error messages hanging and i had to restart it all over again! It is quite a mess and i don't know what to do to clean it up.

'Fatal: Module battery not found' - This is a message that everyone gets after installing the updates, it does not cause any issues and is nothing to worry about as far as I have found. As for the other errors I am not sure. Have you tried a factory restore? This may be your best option now that you have updated the bios. Just so you know after a factory restore you WILL NOT have to re-update the bios. Also if you go to the link in my signature there is a guide to restore with an image from sylvania that might be a little more up to date than the restore image already on the meso. Hope this Helps.

---

### Post by keeptrying1188 on 2009-02-03
Again thanks for your explanation and suggestion to do a factory restore with your restore image. Unfortunately i'm using MAC OS X and not Windows so is there anyway i can do it with my MAC to make the USB drive stick bootable? Your instruction would be most appreciated.

---

### Post by the3dman on 2009-02-03
> **keeptrying1188 said:**
> Again thanks for your explanation and suggestion to do a factory restore with your restore image. Unfortunately i'm using MAC OS X and not Windows so is there anyway i can do it with my MAC to make the USB drive stick bootable? Your instruction would be most appreciated.

Unfortunately not that I know of. You could try to run the makeboot.bat file on your flash drive with crossover office if you have it. Or you can install a xp virtual machine with virtual box. Or possibly a work, friends, library, or school computer? Sylvania has not released the final image yet, so this is the only way until they release it.

---

### Post by eyeofliberty on 2009-02-04
I just bought a G Meso from Amazon today, in solar yellow! I've been watching the price drop from $349, to $299, to $269, which I bought it at. Can't wait to get it. I hope Amazon isn't serious about the 1-2 month ship time...

---

### Post by mttnry on 2009-02-05
Congrats to all the new meso owners and expecting owners :P  I havent checked this thread for a bit but I just caught up.  From what I was reading some ppl were having problems with open office spell check.  I had a similair problem with my desktop ages ago, so when spell check wasnt working on my meso I did the same fix that I did then.  Open office uses the myspell package for its spell check, so if you install that you should be set. for the terminal lovers out there this should work:
sudo apt-get install myspell-en-us

also some one had a problem finding the synaptic package manager I think they resolved it but for anyone else its preferences>main menu>administration> then just check synaptic package manager.  

hope that was helpful.  props to the3rdman and others for being an awesome resource on the meso. 

later days,

---

### Post by gtrtx on 2009-02-07
Hello everybody.

I just purchased the Sylvania G Meso Netbook and so far I'm pretty pleased with it. 

There are a couple issues that I'm experiencing and if someone could help me out that would be great. Especially those that have installed Ubuntu 8.10. 

I've tried several installs. Starting of course with the default. In that mode everything works as it should, but I was experiencing random lock ups when viewing videos. Also when resuming from suspend sometimes the system would be very sluggish. 

I then tried just a plain 8.10, which surprisingly works very well. Even though the kernel isn't lpia it seemed a bit more snappier. No lockups and it has all the software that I want/need. About my only issue with it is that it won't properly wake from suspend. I can live without it, but it would really be nice if I could get it working as it should. I did install the bios update when I had the default OS installed(Hardy-Remix). 

On another note, I also tried lpia version of 8.10. You have to jump through some hoops to get it installed and after installing it, it didn't seem to perform as well as standard 8.10. 

One other small issue is that I get a faint buzzing through the speakers when I plug headphones in. It's not that loud, but I could see how it might annoy others in a quiet environment(a library). I've not found a way to resolve that. I honestly don't know if it behaved this way with the original install or not. Where I normally use it, it's not going to be an issue as it's fairly noisy. 

Overall I'm pleased. I've been a long-time Ubuntu/Linux user and bought the Sylvania for the simple fact that it came with Ubuntu and the price was right. I'll keep tinkering with it and report back if I figure how to fix the suspend issue. 

regards,

---

### Post by gtrtx on 2009-02-07
Howday all,

just wanted to report back. I googled and grepped and found a solution for the issue regarding the G Meso not waking from suspend in Ubuntu 8.10. I checked bugs.launchpad.net and found this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267401]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267401")

which linked to this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274734]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274734")

 It all has to do with the wireless adapter module: rt73usb. The second bug report contains a link to a script that you place in /etc/pm/sleep.d/
and make executable. Also note that the script was originally written for a different module but for the same reason. Because of this the script does have to be edited to reflect the correct driver(rt73usb). 

I've tested this several times and it seems to work flawlessly. 

Sorry for the long-winded post. Hopefully this will help somebody, I know I could have used it when I was trying to figure this out. I'm off to do more tweaking to my new toy!

---

### Post by the3dman on 2009-02-08
> **gtrtx said:**
> Howday all,

just wanted to report back. I googled and grepped and found a solution for the issue regarding the G Meso not waking from suspend in Ubuntu 8.10. I checked bugs.launchpad.net and found this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267401]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267401")

which linked to this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274734]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274734")

 It all has to do with the wireless adapter module: rt73usb. The second bug report contains a link to a script that you place in /etc/pm/sleep.d/
and make executable. Also note that the script was originally written for a different module but for the same reason. Because of this the script does have to be edited to reflect the correct driver(rt73usb). 

I've tested this several times and it seems to work flawlessly. 

Sorry for the long-winded post. Hopefully this will help somebody, I know I could have used it when I was trying to figure this out. I'm off to do more tweaking to my new toy!

Thanks for the info, I use 8.10 also and it is ok, I just don't like that because it is not lpia some of the non-lpia programs don't display to well on the small screen, also the bluetooth is very unreliable too. I have been kinda waiting for an official 8.10 UNR to be released with the lpia kernel, I did try the one that is already out made for MID's but did not work to well for me. Hopefully Sylvania and Canonical will team up soon to make it. Sylvania has been telling me for months that they will release a new image on their site at the end of the month, but it has not happened as of yet.

---

### Post by gtrtx on 2009-02-09
> **the3dman said:**
> Thanks for the info, I use 8.10 also and it is ok, I just don't like that because it is not lpia some of the non-lpia programs don't display to well on the small screen, also the bluetooth is very unreliable too. I have been kinda waiting for an official 8.10 UNR to be released with the lpia kernel, I did try the one that is already out made for MID's but did not work to well for me. Hopefully Sylvania and Canonical will team up soon to make it. Sylvania has been telling me for months that they will release a new image on their site at the end of the month, but it has not happened as of yet.


I agree in regards to some of the non-lpia software not displaying correctly although I've pretty much ironed most of that stuff out.  I also don't think that the battery life is as good without the lpia kernel. I've been using powertop and other laptop tweaks to try to extend the battery life without too much luck. 

Do you know if it's possible to purchase an extra battery from Sylvania?

I tried the live MID's and also a full install of the alternate iso. It was a bit of a pain to install and after I got it installed I just kept trippin up over little random issues here and there. 

Overall I'm quite pleased with the performance using just the standard 8.10. I had alot of wireless networking problems with the default Hardy install as it was just painfully slow. With 8.10 those problems went away, which is one of the big reasons I bought this device(to access my media in different parts of the house). 

One last question. I've been reading elsewhere that its heat that kills the batteries in these things. That it's better to remove the battery when on AC power. Does the same apply for the Sylvania? Is it safe to run it without the batter installed when on AC power?

Regards

---

### Post by wabster on 2009-02-10
My G Meso is loosing roughly five to ten minutes a week of battery life from full charge to shutdown. When I first got it I was getting about 3:20 and now it is down to 2:40. I usually empty the battery after two days of use and then immediately fully recharge overnight. Is anyone else experiencing this?

---

### Post by gtrtx on 2009-02-10
> **wabster said:**
> My G Meso is loosing roughly five to ten minutes a week of battery life from full charge to shutdown. When I first got it I was getting about 3:20 and now it is down to 2:40. I usually empty the battery after two days of use and then immediately fully recharge overnight. Is anyone else experiencing this?


While I don't claim to be an expert, I have been doing a bit of research in trying to extend my battery life. I also have only had mine for just over a week, so of course things may be different for me several months from now. That being said, I have read that you shouldn't completely drain the battery very often. But about once a month you need to calibrate the battery. I don't actually have specifics, but if you do a Google search you will find plenty if information.   

I find the battery readings to be sporadic. Usually when it's fully charged it reads that it has 2:50. Today it says 3:05. So I'm still trying to figure this all out. If I get any more info, I'll certainly be sure to share.

regards

---

### Post by keeptrying1188 on 2009-02-10
For those of you who are interested in the G-Meso replacement batteries you can contact:

Christa Kraft
Levin Consulting
216.595.9828 x110

23950 Commerce Park
Beachwood, OH 44122
[email]christak@levinconsulting.com[/email] 

You'll have to tell her the color of your G-Meso to match the battery. Hope this helps. Good luck.

---

### Post by the3dman on 2009-02-10
I thought I had battery problems when I first got mine, then I figured out that a battery will never hold what it was designed to hold, and eventually my battery life stopped dropping and stays the same everytime I use it now. (Design charge is 35.5Wh and my battery settled at 31.9Wh for a full charge)

The heat killing the battery I have never heard of except from extreme heat which the meso does not put out. I could be wrong though.

By the way thanks for the post on where to get the spare batteries very helpful!

---

### Post by fetisha on 2009-02-16
Just bought one two days ago and loving it so far. The cam problem was an easy fix when I sent to the Sylvania website and downloaded the bios and cam fix files. Java on there is kind of blah, I tried installing Sun Java 6 and making it the default, but it didn't work. Don't think the install worked either, 'cause it didn't ask me to accept any licenses and whatnot. Also, with UNR some of the softwear sources don't work I've noticed. I was wondering, I'm not a fan of the remix layout and switched the look back to the regular ubuntu feel, is it advisable to just install Ubuntu 8.10 or Kubuntu on here? Anyone tried it? Will it slow the computer down?

---

### Post by fetisha on 2009-02-16
> **gtrtx said:**
> Howday all,

just wanted to report back. I googled and grepped and found a solution for the issue regarding the G Meso not waking from suspend in Ubuntu 8.10. I checked bugs.launchpad.net and found this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267401]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267401")

which linked to this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274734]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274734")

 It all has to do with the wireless adapter module: rt73usb. The second bug report contains a link to a script that you place in /etc/pm/sleep.d/
and make executable. Also note that the script was originally written for a different module but for the same reason. Because of this the script does have to be edited to reflect the correct driver(rt73usb). 

I've tested this several times and it seems to work flawlessly. 

Sorry for the long-winded post. Hopefully this will help somebody, I know I could have used it when I was trying to figure this out. I'm off to do more tweaking to my new toy!

saved it on my desktop, made it executable and tried to move it to that folder but it gives me an error when moving it. Am i supposed to save is as a specific extension or name?

---

### Post by gtrtx on 2009-02-16
> **fetisha said:**
> saved it on my desktop, made it executable and tried to move it to that folder but it gives me an error when moving it. Am i supposed to save is as a specific extension or name?

Have you installed 8.10? If not, i wouldn't bother with the script. If I recall correctly, suspend works with the default Hardy remix installation providing the BIOS update has been installed.

If you do have 8.10 installed you do need to move it to the 
/etc/pm/sleep.d/ folder using sudo. Also, make certain that you've edited the file to reflect the rt73usb.

Again, this is for 8.10. If you haven't installed 8.10, script isn't necessary. 

Also keep in mind that 8.10 isn't really supported as it doesn't use the lpia kernel. I have found, however, that it runs pretty good. I actually prefer it. I certainly wouldn't say that it was slower. It may not be as efficient in regards to battery usage. I really didn't use the default install long enough to compare the two. the3dman, may be able to provide more info regarding that.

If you need more specific help....just hollar

---

### Post by tdwester on 2009-02-17
I am having a problem with the wireless on my meso netbook. The ranfe seems to be pretty poor and transfer speed is also fairly poor. I was wondering if anyone else is having this problem or have found a solution to this?

---

### Post by gtrtx on 2009-02-18
> **tdwester said:**
> I am having a problem with the wireless on my meso netbook. The ranfe seems to be pretty poor and transfer speed is also fairly poor. I was wondering if anyone else is having this problem or have found a solution to this?

I also didn't have very impressive wireless performance when using the default software(Hardy). Upgrading to 8.10 fixed that. The wireless performance issues disappeared. 

I did have some issues in 8.10 keeping a connection when transferring large files or watching video over my wireless network, but now that seems to be fixed. Bad thing is, I did so many things, I'm not sure exactly what fixed it. 

As I've stated in my previous posts, 8.10 isn't supported and doesn't have a lpia kernel. I do have to say, however, for me the performance trade off was well worth it.

---

### Post by greyfox1 on 2009-02-18
I've also been having issues with extremely slow wifi connection speeds.  I wrote to Sylvania support last week with the following:

> I'm having problems with the wifi on my Meso G.  It seems that no matter what I do, the connection speed is very erratic.  Often when I'm downloading something, the connection slows to less than 1 kbps or stops completely (although I remain connected to the network).  Overall, I see more of this extreme slowness than I see acceptable speeds.

I have tried this from my home network (where I experimented with various settings without success) as well as my wireless network here at the office.

I have also tried restoring to factory from the restore partition (two or three times) and that hasn't produced any change either.

Any help, suggestions, and/or fixes would be GREATLY appreciated.

Here is the response I got:

> Hope all is well, recently this has been a common issue that people have been experiencing. We Have 3 MESO machines 2 with Ubuntu and 1 with XP. We tested all 3 machines and both MESO with the linux OS seems to be maxing out at a 1mb download speed over wireless. When testing the windows XP, its seems to be running at normal/faster speeds. This is an issue we are closely observing and seeking for a solution. We are thinking that it might be the specific wireless card and its compatibility with the LINUX OS, We are working to see if we can have an update to fix this solution. Once we have more information you can visit the digital gadgets website for any possible updates. Thanks for your patience.

So they are at least working on it.  Hopefully there will be a fix or patch of some sort soon.  I came here to post this and I see that gtrtx has had success in working around it by upgrading to a standard 8.10 installation.  Maybe I'll give that a whirl.  Hopefully the wifi issues will be resolved with the standard Jaunty version of Netbook Remix so we won't have to trade a bit of performance for reliable wifi!

---

### Post by tdwester on 2009-02-19
I talked to them on the phone and they did say they were working on it the nice thing is they called me back a couple hours later which was shocking in it self, and they were talking to the manufacture and should have fix in a couple of weeks. There customer service seems top notch!

---

### Post by greyfox1 on 2009-02-19
That's awesome to hear.  When I wrote in, they at first wrote back and asked if they could call me (unusual too) but since I work while they are open I declined and opted to keep it confined to email.  They seemed very good to me too-- not the typical script-reading drones that you usually get.

:D

---

### Post by bigal480 on 2009-02-19
This is a great simple machine.  I'm not a big fan of UNR version after about 3 weeks of use.  I upgraded to 8.10 however the webcam does not work.  The netbook does not see the driver either when running the lsusb.  Any fix or driver to download?

---

### Post by bigal480 on 2009-02-19
Nevermind.  I installed the UNR repositories for 8.10.  No issues so far.....

---

### Post by the3dman on 2009-02-20
Hi everyone sorry I have been gone for a while, I see some people are still having trouble with the wireless. I have a solution that may work. It involves upgrading your network manager from the one in UNR 8.04 to the network manager from 8.10. Here is the link to the guide I posted: [http://forum.lowpowertech.com/viewtopic.php?f=6&t=9&p=10#p10](http://forum.lowpowertech.com/viewtopic.php?f=6&t=9&p=10#p10)

I must give thanks to Darrena for originally posting this. I merely edited it to make it very easy to follow on the meso g. Hope This helps

---

### Post by rick71 on 2009-02-21
Does anyone know if it is possible to swap the Meso g's keyboard? I was looking at the original Meso keyboard and it looks like it has a much better layout.

---

### Post by the3dman on 2009-02-21
> **rick71 said:**
> Does anyone know if it is possible to swap the Meso g's keyboard? I was looking at the original Meso keyboard and it looks like it has a much better layout.

I really don't think so, According to the spec's they are different sizes.

---

### Post by gtrtx on 2009-02-21
Does anyone know if adding additional RAM is a possibility?

I know that there are no easily accessible compartments and the unit would have to be taken apart. Just wondering if anybody has opened it up and looked inside.

That being said, thus far the performance w/ the existing RAM has been good, but it'd be nice to know if upgrading to 2 GB is possible.

---

### Post by wp2022 on 2009-02-21
I recently installed Intrepid (the i386 version) on my Meso, it isn't the lpia version and i'm not sure i'm going to add those repositories. There may have been imperceptible losses in terms of boot up speed and/or battery life, but the gains have been that Compiz now works now -- love the eye candy! Also, i recently upgraded to a Rev A EVDO card.  With Intrepid, the Broadband connection worked automatically, zero configuration necessary! (after activating the card on a Windoze machine).

---

### Post by gtrtx on 2009-02-21
> **wp2022 said:**
> I recently installed Intrepid (the i386 version) on my Meso, it isn't the lpia version and i'm not sure i'm going to add those repositories. There may have been imperceptible losses in terms of boot up speed and/or battery life, but the gains have been that Compiz now works now -- love the eye candy! Also, i recently upgraded to a Rev A EVDO card.  With Intrepid, the Broadband connection worked automatically, zero configuration necessary! (after activating the card on a Windoze machine).

I agree. With Intrepid everything seemed to work better out of the box. The only thing that I had issues with was getting the Meso to wake from suspend or hibernate. I've straightened that out(I explained how several posts back, If you need any clarification I'll be happy to help). 

I also like the eye candy.I have compiz enabled and it works well. I will say that I'm using it sparingly without all the same bells and whistles that my desktop(w/ nvidia GPU) has.  

I've also installed Swiftfox as it seems a bit more responsive and has a smaller memory footprint than Firefox. 

And one last thing you may want to check into is powertop. It's in the repos and it helps squeeze a little more life out of the battery.

---

### Post by greyfox1 on 2009-02-22
> **the3dman said:**
> Hi everyone sorry I have been gone for a while, I see some people are still having trouble with the wireless. I have a solution that may work. It involves upgrading your network manager from the one in UNR 8.04 to the network manager from 8.10. Here is the link to the guide I posted: [http://forum.lowpowertech.com/viewtopic.php?f=6&t=9&p=10#p10](http://forum.lowpowertech.com/viewtopic.php?f=6&t=9&p=10#p10)

I must give thanks to Darrena for originally posting this. I merely edited it to make it very easy to follow on the meso g. Hope This helps

I followed this but wifi is still slow as molasses for me.  I still can't surf the net using my netbook. ARGH!

---

### Post by the3dman on 2009-02-22
> **greyfox1 said:**
> I followed this but wifi is still slow as molasses for me.  I still can't surf the net using my netbook. ARGH!

What security are you using to encrypt the wireless. Try using an unsecured wireless connection temporarily and see if this changes your speed, if it does then maybe try a different type of wireless security.

---

### Post by the3dman on 2009-02-22
> **gtrtx said:**
> Does anyone know if adding additional RAM is a possibility?

I know that there are no easily accessible compartments and the unit would have to be taken apart. Just wondering if anybody has opened it up and looked inside.

That being said, thus far the performance w/ the existing RAM has been good, but it'd be nice to know if upgrading to 2 GB is possible.

I have heard that this is possible but, I have opened my meso, and even after opening the ram does not seem to be easily accessible. I did not want to play with it that much, the stock ram is good for me.

---

### Post by wp2022 on 2009-02-23
thanks for the input -- i will avoid the lpia repo's then.  I am trying to get the suspend issue fixed but no luck so far -- i edited the file, replacing the previous driver with rt73usb, made it executable and put it in the etc/pm/sleep.d/ directory, but the system still freezes when waking up, i have to shut it down and reboot.  Might it be that i am using the usb 3G card and not the onboard wifi?  and if so, any idea how to fix?

thanks




> **gtrtx said:**
> I agree. With Intrepid everything seemed to work better out of the box. The only thing that I had issues with was getting the Meso to wake from suspend or hibernate. I've straightened that out(I explained how several posts back, If you need any clarification I'll be happy to help). 

I also like the eye candy.I have compiz enabled and it works well. I will say that I'm using it sparingly without all the same bells and whistles that my desktop(w/ nvidia GPU) has.  

I've also installed Swiftfox as it seems a bit more responsive and has a smaller memory footprint than Firefox. 

And one last thing you may want to check into is powertop. It's in the repos and it helps squeeze a little more life out of the battery.

---

### Post by gtrtx on 2009-02-23
Just out of curiosity, have you tried removing the 3G card prior to suspending the netbook? If your not using the onboard wifi, you could probably just disable it altogether.  

Also, I know that there is a BIOS update from Sylvania that addresses suspend issues. I've read that you can't apply it unless your using the OS that came with the unit. I updated my BIOS when I first got the thing when it had the default software installed. I believe the latest bios is version 3.5. You might check that.

---

### Post by wp2022 on 2009-02-24
Nope, pulling the card out didn't make any difference.

And i never was able to install the BIOS upgrade -- it just didn't do anything on the original software, when i talked to tech support they seemed vexed about why it wouldn't work (they did say it had to be applied as root, which i can't do in lipa hardy because in the process of installing intrepid, my recovery partition got overwritten). Going back to the original config isn't an option unless someone knows how to get an ISO of the recovery partition.

i don't really need suspend anyway, just a few situations where it would be handy.

---

### Post by wp2022 on 2009-02-24
...  oops.  i am actually running Version 3.5 of BIOS (guess that would be why it wouldn't update!)

really should check all the details before i post

---

### Post by gtrtx on 2009-02-24
When I get a chance, I'll look through my notes to see if I did anything else to get suspend working. I really only recall adding the script.

Now, I know alot of folks suggest to install the backport modules(when I was researching issues with my wifi). When I did this, it broke suspend so I removed it. 

One thing you might try is manually removing the rt73usb prior to suspending:
```

sudo rmmod rt73usb
```

Then after waking(if it does wake that is)

```
sudo insmod rt73usb
```

That's how I learned that the rt73usb was not allowing the netbook to resume from suspend. If this doesn't work for you you may have another issue altogether.

I was about ready to live without suspend, but using the netbook is so much nicer with it.

---

### Post by wp2022 on 2009-02-24
Success!

running  that code from terminal did the trick.  wish i could get that code to do it automatically though -- does it matter what i name that file?  I just used the 50zd1211, as that's what it was named in the link you had put.  And should it be .htm, or some other extension?

---

### Post by gtrtx on 2009-02-24
Cool, the script should take care of it.

While I don't think the name of the file should really matter I renamed mine to 50rt73usb.  It doesn't have an extension and I made it executable with:

```
sudo chmod +x /etc/pm/sleep.d/50rt73usb
```

The contents of the file are as follows:

```
#!/bin/bash
case $1 in
    hibernate)
        echo "S2D ; stopping NM before removing zd1211 module"
	/etc/init.d/NetworkManager stop
	rmmod rt73usb
        ;;
    suspend)
        echo "S2R ; stopping NM before removing zd1211 module"
	/etc/init.d/NetworkManager stop
	rmmod rt73usb
        ;;
    thaw)
        echo "resuming from S2D"
	modprobe rt73usb
	sleep 1
	/etc/init.d/NetworkManager start
        ;;
    resume)
        echo "resuming from S2R"
	modprobe rt73usb
	sleep 1
	/etc/init.d/NetworkManager start
        ;;
    *)  echo "somebody is calling me totally wrong."
        ;;
esac
```

That way you can check what you have against what I have.

Hopefully that will be of some help.

Oh, and how are you putting the netbook into suspend? Through gnome powermanager? Issuing a command? Hotkeys on keypad?

It really shouldn't make a difference, but at one time I had a configuration where it would work through the gnome power manager but not the hotkeys. I'm actually not sure what I did, but that is no longer the case.:confused:

---

### Post by wp2022 on 2009-02-24
finally got it working -- i must have had a typo somewhere -- the code you posted is  what i had -- but it is very possible that when i edited the file to replace the other name with rt73usb i didn't save it

thanks for all the help!

---

### Post by gtrtx on 2009-02-24
Cool....Glad you got it workin!

---

### Post by the3dman on 2009-02-25
> **wp2022 said:**
> Nope, pulling the card out didn't make any difference.

And i never was able to install the BIOS upgrade -- it just didn't do anything on the original software, when i talked to tech support they seemed vexed about why it wouldn't work (they did say it had to be applied as root, which i can't do in lipa hardy because in the process of installing intrepid, my recovery partition got overwritten). Going back to the original config isn't an option unless someone knows how to get an ISO of the recovery partition.

i don't really need suspend anyway, just a few situations where it would be handy.

If you go to the link in my signature there is a post with the link to the stock recovery and regular partition in a zip file with easy instructions on how to restore.

---

### Post by qkall on 2009-03-03
something that may help those with wireless issues...

for whatever reason... wap2 would not work with 8.04 even with remix repo's AND the network manager PPA that the3rdman suggests upgrading to (tho this did help with my tethering issues)... so i figured what the hell and tried 8.10... works flawlessly (not sure if the remix repo was needed, but kept it due to it helping my webcam working previously)

---

### Post by keeptrying1188 on 2009-03-08
Does anyone have any idea how to set up firewall when using the internet or when surfing the net on a public network? Is there a firewall setting for UNR? Please help. I am worried about security.

---

### Post by qednick on 2009-03-09
I got tired of waiting for Amazon to ship out my G Meso so cancelled it and decided to pay more and ordered the last one MacMall had in stock instead. Should get it in 2 days so can't wait!!

This thread has some very interesting stuff in it. I'm looking forward to adding my 2 cents (issues/solutions) on this little machine once I receive it.

Anyways, just wanted to thank everyone for the input on this thread so far. It's partly due to this thread (and user reviews elsewhere) that I decided on the G Meso!! :D

---

### Post by gtrtx on 2009-03-09
> **keeptrying1188 said:**
> Does anyone have any idea how to set up firewall when using the internet or when surfing the net on a public network? Is there a firewall setting for UNR? Please help. I am worried about security.

There's an application in the repositories called firestarter. I've not really used UNR so I honestly couldn't say if it's available, but I would think it should be. 

I've never used firestarter as Linux/Ubuntu is pretty secure out of the box. I've yet to have any problems. 

When at home I have a firewall/router that's locked down fairly tight.

---

### Post by the3dman on 2009-03-11
I have used firestarter on my desktop for a long time, but never on UNR. I will give it a shot and report back though.

---

### Post by the3dman on 2009-03-12
Just an update I tried Firestarter on the meso, and it works great with no issues for me, so  if you need a firewall it should work well for you.

---

### Post by qednick on 2009-03-12
Well I finally got my Meso G by FedEx today! :D

This thing is BRILLIANT!! And if it isn't the cutest little thing I've ever seen too!

The first thing I did was install the BIOS upgrade. Web cam now works fine. Everything else works fine too so far. It is very solidly built. It almost feels like a tiny "toughbook". 

I haven't had any issues with noise, fans or anything like that (including with AC adapter in). I've yet to discover how much battery life I get out of it.

The mouse buttons do click somewhat but don't forget you can always click the mousepad (silently) instead. Either way, I would attribute the clicking to just how solid this thing is built.

After reading some reviews on Amazon and elsewhere, I'm surprised some people complained about tinny sound and the small keyboard. I think the sound and keyboard are perfectly acceptable for something that's not much larger than a Nintendo DS!!

I've yet to try plugging a VGA monitor in or anything else for that matter.

Anyways, just thought I'd give my 2 cents worth in case anyone else is considering buying one of these little beauties. I would HIGHLY recommend it!! Especially for the money!!

**EDIT**

Hmmm, once I got my meso home I started having trouble keeping it on the wireless network (worked fine at the office but was about 3 feet away from the AP). When it was on the network it was VERY slow (worse than dial-up). I confirmed this by walking upstairs and towards the AP while performing a download - it went from approx 12K/s to 1000K/s

I followed the instructions posted earlier about updating the network manager to the one used in 8.10 which did make a significant difference. However, it's still not perfect and does lose connection or act very slow on occasion. 

I then tried upgrading to 8.10 but can't figure out how. I went System->Administration->Software SOurces->Updates and put "show new distro releases" to "Normal Releases". Then I ran the updater but it says no updates available - and I'm still on 8.04
Can anybody tell me how to do this on the meso?

**EDIT** (again)
Well I managed to upgrade to 8.10 with the regular i386 ISO and a USB memory stick. This seems to have cured the wireless issue. 
On another note, I plugged in my Cricket Broadband USB Modem and I was surprised just how well 8.10 took it. It was recognized straight away and I simply had to use Network Manager to put my Cricket username/pass in it and I was up and running with high speed internet mobile style!!
Overall, despite the initial wireless issue (now cured) the meso is a KILLER machine. Little wonder they're so hard to purchase. The price is right, they're well built and ubuntu rocks on these things. Perhaps Sylvania is having trouble making them fast enough!!

---

### Post by gtrtx on 2009-03-15
> **qednick said:**
> 
Well I managed to upgrade to 8.10 with the regular i386 ISO and a USB memory stick.

I was just checking the thread, and was going to recommend that you use a USB flash drive. You beat me to it. 

As I've mentioned several times, 8.10 just seems to perform better all around. The only thing that really didn't work for me in 8.10 was the suspend and hibernate. I got that sorted and posted how earlier in this thread.

Glad you like your new netbook and if you need any help with anything, just holler! :D

---

### Post by muzincs on 2009-03-15
Hello everyone.  First, THANKS to everyone in this forum.  My new Meso would have been a pain in the neck were it not for this forum.

Got my Meso delivered from RCS Experience (listed on the Sylvania website) 2 days ago for $249, an incredible deal.  It is bright yellow!  I *love* this little machine.  I was afraid that my expectations were too high because of the good reviews.  But, no, it is really wonderfully well put together and so light!  I suspected it would be a returned item even though it was advertised as new, since no one else had them in stock.  Sure enough, someone had already updated the software for the webcam, but forgot to remove the plastic cover on the lens...  I was very grateful for this forum: otherwise I would not have known how to restore the machine to factory defaults (the first buyer did not forward his/her password). :)

After going through the recovery, I updated the bios and webcam, and updated Hardy, all 166 files.  Then I upgraded the network-manager.  It is working better (wireless connection) but still not nearly as well as my vaio laptop on the same home wireless network.  The viao was also pretty horrible under Hardy.

I installed FBReader and downloaded a bunch of books from Project Gutenberg.  So cool.  I think the Meso works best if you rotate the text 90 degrees and then hold the Meso like a book.  A poor man's Kindle.

I have but one question, and I'm afraid I know the answer.  Everyone says that the wireless connectivity problem goes away with Intrepid.  But if I upgrade to Intrepid I can no longer use UNR, right?  I happen to like UNR a lot.  I think it is a great implementation of Ubuntu for a small screen like the Meso has.  So, any ideas for improving connectivity while sticking to Hardy are most welcome.

Last, are they planning on releasing UNR under Jaunty?

---

### Post by qednick on 2009-03-15
> **gtrtx said:**
> I was just checking the thread, and was going to recommend that you use a USB flash drive. You beat me to it. 

As I've mentioned several times, 8.10 just seems to perform better all around. The only thing that really didn't work for me in 8.10 was the suspend and hibernate. I got that sorted and posted how earlier in this thread.

Glad you like your new netbook and if you need any help with anything, just holler! :D

Thanks gtrtx! Actually I'm still having issues with the whole suspend/hibernate thing (the instructions didn't seem to work for me). Other than that everything seems hunky dory so far with 8.10

I did end up installing myself another AP on my home wireless as a repeater just to give it all a boost - works great now.

I've decided to keep all my photos and music on my server (also ubuntu 8.10) because it's many many gigabytes. I set up sshfs mounts in scripts and added them to my Applications menu for convenience so I can mount and unmount at will. The great thing is I can access/play/view music/photos via rhythmbox, etc. over the internet securely without having to use all the space up on the meso's hard drive. If anybody else wants to do this and needs step-by-steps just give me a shout.

Think I'll take another look at the suspend/hibernate issue now.

:D

---

### Post by qednick on 2009-03-15
> **muzincs said:**
> Hello everyone.  First, THANKS to everyone in this forum.  My new Meso would have been a pain in the neck were it not for this forum.

Got my Meso delivered from RCS Experience (listed on the Sylvania website) 2 days ago for $249, an incredible deal.  It is bright yellow!  I *love* this little machine.  

...

Dang! I had mine on order with amazon (for at least two weeks) and I saw RCS had one yellow one available. I was teetering about thinking about whether to order it or not when all of a sudden they were out of stock. Thankfully I saw MacMall had one snow white one left in stock so that's what I got. So in other words _your_ meso was almost _my_ meso :D

Got myself the smallest laptop bag I could find today (Office Depot). Amazingly, the meso fits in one of the "half" sleeve pockets on the inside of the bag!! Just gotta love these things!!!!! 

As for your remix question... you'll have to decide whether you like it enough to suffer the slow wireless. Personally, speedy wireless is more important to me than the remix.

---

### Post by the3dman on 2009-03-16
Just saw this today, and I will be trying it tonight. I would not recommend it as a full-time option yet, it is probably not stable yet. I will let you all know how it works though.

Ubuntu-Netbook-Remix 9.04 (Jaunty Jackalope)
[http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/jaunty-netbook-remix-i386.img](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/jaunty-netbook-remix-i386.img)

---

### Post by muzincs on 2009-03-16
> **qednick said:**
> Dang! I had mine on order with amazon (for at least two weeks) and I saw RCS had one yellow one available. I was teetering about thinking about whether to order it or not when all of a sudden they were out of stock. Thankfully I saw MacMall had one snow white one left in stock so that's what I got. So in other words _your_ meso was almost _my_ meso :D  

LOL!  This will make you feel better: I was pondering "To buy or not to buy" for about a week.  When I finally decided to take the plunge I went to Amazon where I had seen a white one in stock that morning.  It was gone!  Then yesterday I looked in Amazon again (masochist, I know) and it was back in stock.

The whole point of these little guys is that they are *so* portable, so, yes, I agree with you that wireless connectivity is of the essence.  Here is hoping that the Jaunty/UNR combo is stable enough to install pretty soon.  Else, I think I'll have to follow the instructions on this thread and upgrade to Intrepid asap.

One last thing, with Texas featuring so prominently in this thread, perhaps we should start a meso users group and have ourselves a conference.  :D

---

### Post by the3dman on 2009-03-16
Ubuntu-Netbook-Remix 9.04 (Jaunty Jackalope) - Results

Well it looked nice after installing (Very nice new log on screen), but it has some bugs that render it useless so far. I will hope for better in April! (On a side note the network manager is great in this.)

1) Suspend works when you close the lid, but will not come back on.

2) After switching to classic mode and restarting, the desktop will no longer load. 
3) Still no preloaded support for usb ntfs drives. (Not a huge deal this is easy to fix)
4) Had trouble reconnecting a bluetooth mouse after pairing.

That's about as far as I got (Its hard to work with no desktop! lol). I will report more as I find out more.

---

### Post by qednick on 2009-03-16
So much for everything being bigger in Texas huh? :D  Perhaps we like stuff smaller after all. I love the fact that when I put the meso and charger in the bag it still feels like the bag's empty!

Interesting info on the jaunty remix the3dman. Think I'll wait a bit before trying it myself. I'm actually really happy with the regular desktop anyway. I installed all as i386 and haven't noticed any performance hits at all.

BTW muzincs, if you are planning on trying 8.10, when you go through the setup, make sure you don't choose to use the entire disk (leave it the default setting) and GRUB will still allow you to boot into the previous remix if you want.

Anyways, another update on my experience. I finally got the suspend/hibernate thingy to work in 8.10 thanks to the script posted earlier by gtrtx in this thread. Apparently I made a typo on my little keyboard when I tried it earlier.

Overall, apart from a little tweaking here and there, I really have no complaints about this little machine. Although I do miss the two-finger-trackpad-scrolling that Mac laptops have (that would be really nice).

---

### Post by muzincs on 2009-03-16
> **qednick said:**
> BTW muzincs, if you are planning on trying 8.10, when you go through the setup, make sure you don't choose to use the entire disk (leave it the default setting) and GRUB will still allow you to boot into the previous remix if you want.

...
Overall, apart from a little tweaking here and there, I really have no complaints about this little machine. Although I do miss the two-finger-trackpad-scrolling that Mac laptops have (that would be really nice).

qednick, thanks for that tip.  I would not have known to do that... 
 
I have never owned a Mac so I don't know what two-finger scrolling is.  My vaio scrolls if you slide one finger up and down near the right edge of the mouse pad.  It took me a while to figure out the meso, but I finally did.  To scroll just press (and hold depending on how far you want to scroll) near the top right corner to go up, near the bottom right corner to go down.  It works really well.

After seeing the3rdman's entry earlier today I decided to give Jaunty a try.  I did not put it through its paces, like the3rdman did.  Not sure I know how to!  It is very nice.  In the "home" screen they added a folder for the desktop, which is nice.  In system administration, they added synaptic.  Rythmbox wouldn't play my music, missing codecs.  But the one thing I cared about, wireless connectivity, was just as bad as in my current UNR/Hardy.  :(  :(  Is it possible that trying UNR/Jaunty off of a usb drive would not deliver the same performance than from a real install?

---

### Post by qednick on 2009-03-17
> **muzincs said:**
> qednick, thanks for that tip.  I would not have known to do that... 
 
I have never owned a Mac so I don't know what two-finger scrolling is.  My vaio scrolls if you slide one finger up and down near the right edge of the mouse pad.  It took me a while to figure out the meso, but I finally did.  To scroll just press (and hold depending on how far you want to scroll) near the top right corner to go up, near the bottom right corner to go down.  It works really well.


Dang, didn't know that - I've been using the arrow keys. I also love the fact you can zoom in and out on web pages.

> **muzincs said:**
> 
After seeing the3rdman's entry earlier today I decided to give Jaunty a try.  I did not put it through its paces, like the3rdman did.  Not sure I know how to!  It is very nice.  In the "home" screen they added a folder for the desktop, which is nice.  In system administration, they added synaptic.  Rythmbox wouldn't play my music, missing codecs.  But the one thing I cared about, wireless connectivity, was just as bad as in my current UNR/Hardy.  :(  :(  Is it possible that trying UNR/Jaunty off of a usb drive would not deliver the same performance than from a real install?

It probably won't give you same performance running off a usb stick but I'm no expert. Personally I'm just going to wait till they get all the bugs ironed out before I try it. I would recommend trying 8.10 though - seems to work very well including the wireless. You just won't have the remix desktop (until they iron it out). To me it's a small price to pay.

---

### Post by muzincs on 2009-03-17
How do you zoom in and out?  I've been using ctrl+ and ctrl-.  Is there a better way?

---

### Post by qednick on 2009-03-17
> **muzincs said:**
> How do you zoom in and out?  I've been using ctrl+ and ctrl-.  Is there a better way?

No, you got it right. I like the fact it enlarges everything, not just the text. Great on a small screen when you have bad eyesight like me! ;)

I tried the trackpad scrolling which is cool but I think I'll stick to the arrow keys - seems more controllable for some reason. I don't recall seeing any settings where I can adjust the sensitivity of that feature. Maybe it just takes practice?

---

### Post by muzincs on 2009-03-17
Yes, it does take a little practice to get the exact amount of scrolling you want.

I decided to bite the bullet and install Intrepid.  It took me 6 hours #!%!# to get the usb stick to work.  After trying with three different ones, and much, much searching online, I finally found a solution to "Invalid or Damaged boot partition" that worked.  In case anyone else is trying to install Intrepid on the meso and runs into the same problem, here is the link:

[http://ubuntuforums.org/showthread.php?t=965854](http://ubuntuforums.org/showthread.php?t=965854)

Things didn't work for me quite like CJWertz reports in his/her posting. Basically you have to wipe out the existing partition on the USB stick and leave it like that.  Then, when you start Create a USB Startup disk it will say the stick needs to be formatted.  Say yes, and everything works from that point forward.

qednick, I have three other machines that are dual boot to XP, so I don't know why it hadn't occurred to me to leave UNR/Hardy on the disk...  Thanks again for pointing it out.  

Intrepid is installing on the meso as I type this posting (on my desktop).  Here is hoping the wireless problem will go away for good!  :D
Will report back if it does (and ask for more help if it does not).

---

### Post by bellarue on 2009-03-17
Add another Texan to the list of owners! I have been lurking for awhile and just got my MESO yesterday!  So far, I absolutely love it!!!!  This is my first venture away from Windows....very liberating!  I have already used the info on this thread to get things going.  Everything seems to working great, including wireless connection! I do have one concern, however. My Meso came from RCS experience and was an open box item.  It sounds like there is something rolling around inside the case, like a tiny metal screw or something.  Should I look inside?

---

### Post by muzincs on 2009-03-17
Hi Bellarue and welcome to the thread!  (We really should start a Texas meso users group.)  Glad to hear you got the wireless working.  Re the noise in the box, I am clueless.  You may have to wait a little, but I am sure one of the experienced folks in this forum will chime in eventually.

---

### Post by qednick on 2009-03-17
> **muzincs said:**
> Yes, it does take a little practice to get the exact amount of scrolling you want.

I decided to bite the bullet and install Intrepid.  It took me 6 hours #!%!# to get the usb stick to work.  After trying with three different ones, and much, much searching online, I finally found a solution to "Invalid or Damaged boot partition" that worked.  In case anyone else is trying to install Intrepid on the meso and runs into the same problem, here is the link:

[http://ubuntuforums.org/showthread.php?t=965854](http://ubuntuforums.org/showthread.php?t=965854)

Things didn't work for me quite like CJWertz reports in his/her posting. Basically you have to wipe out the existing partition on the USB stick and leave it like that.  Then, when you start Create a USB Startup disk it will say the stick needs to be formatted.  Say yes, and everything works from that point forward.

qednick, I have three other machines that are dual boot to XP, so I don't know why it hadn't occurred to me to leave UNR/Hardy on the disk...  Thanks again for pointing it out.  

Intrepid is installing on the meso as I type this posting (on my desktop).  Here is hoping the wireless problem will go away for good!  :D
Will report back if it does (and ask for more help if it does not).

Dang, it shouldn't have been quite so troublesome. I was up and running with the update in no time. Perhaps should've posted a step-by-step to make it easier. Sorry!

> **bellarue said:**
> Add another Texan to the list of owners! I have been lurking for awhile and just got my MESO yesterday!  So far, I absolutely love it!!!!  This is my first venture away from Windows....very liberating!  I have already used the info on this thread to get things going.  Everything seems to working great, including wireless connection! I do have one concern, however. My Meso came from RCS experience and was an open box item.  It sounds like there is something rolling around inside the case, like a tiny metal screw or something.  Should I look inside?

Welcome to the foums bellarue! I have a similar loose screw problem with my head... but I think I'm way past my warranty. If I were you I'd give them a call about it. The only drawback is if you have to send it back you'll be without it for a time while they look at it. :(

Anyways, good to hear you're liberated! Don't forget, you can always run Windows on your Linux machine by installing the freely available "VirtualBox". This may help with your transition. However, best to try and do most things in your new OS wherever possible. It will take a while to get used to the new surroundings but, believe me, once you've gotten used to it, you'll never look back (ahh those good old days of 4 minute boot up times, keeping up to date with all the latest anti-virus, anti-malware, anti-spyware, anti-trojan subscriptions that slow your brand new PC to a crawl - oh and let's not forget the dreaded blue screens!). Yup... I used to be a Windows programmer - which is why I avoid it like the plague now!! I suppose when you have as much money and pure marketing clout as MS, it's easy to sell ice cubes to eskimoes. ;)

---

### Post by muzincs on 2009-03-17
Hi qednick.  OK, the meso is now running on Intrepid.  Wireless is much better, but when it is sitting side-by-side with the vaio (also on Intrepid) it connects about half as well (47% vs 89%).  Go figure.  Any thoughts?

I installed Skype but I haven't got it to work yet (problem with audio capture).  Also, Cheese seems to be gone.  Do you know where it went?

---

### Post by gtrtx on 2009-03-18
Cheese doesn't install in Intrepid by default, I don't think anyway.

You can add it, from a terminal

```
sudo apt-get install cheese
```

Or through add/remove programs.

I've not had any experience with skype, but in getting other Audio programs to capture the mic in Intrepid I've had to make sure that the proper mic was chosen in my audio mixer(double click on the little speaker on the taskbar)

---

### Post by gtrtx on 2009-03-18
> **qednick said:**
> 
I've decided to keep all my photos and music on my server (also ubuntu 8.10) because it's many many gigabytes. I set up sshfs mounts in scripts and added them to my Applications menu for convenience so I can mount and unmount at will. The great thing is I can access/play/view music/photos via rhythmbox, etc. over the internet securely without having to use all the space up on the meso's hard drive. If anybody else wants to do this and needs step-by-steps just give me a shout.

I have things setup this way over my local network using sshfs. Everything works quite well. I'm even streaming live TV from my desktop with a tv tuner card. 

Over the internet, however, I'm not having the same luck. I can mount shares over the internet and access my files, but not get them to play through a media player.  I just attributed it to a bandwith issue. If there is a way to overcome this I'm interested.

---

### Post by qednick on 2009-03-18
> **muzincs said:**
> Hi qednick.  OK, the meso is now running on Intrepid.  Wireless is much better, but when it is sitting side-by-side with the vaio (also on Intrepid) it connects about half as well (47% vs 89%).  Go figure.  Any thoughts?

I don't think netbook wireless cards are as good as full size ones. I've spoken to a couple of others and seen reviews (for other makes of netbooks) that pretty much say the same thing. I'm pretty tempted to try a USB wireless card just to get the extra boost but I don't really want stuff sticking out the side of my toy.

> **gtrtx said:**
> Over the internet, however, I'm not having the same luck. I can mount shares over the internet and access my files, but not get them to play through a media player.  I just attributed it to a bandwith issue. If there is a way to overcome this I'm interested.

Hmmm good point. I've only messed with this at home where the server is (even though I accessed it using the WAN address and not the LAN address). I'll try it tomorrow from the office to see. I would try it with my cricket modem right now but I get the worst signal from home (faster than DSL when in town) so that really wouldn't tell me much.

Which media player are you using? I'm using Rhythmbox.

---

### Post by muzincs on 2009-03-18
> **gtrtx said:**
> Cheese doesn't install in Intrepid by default, I don't think anyway.

You can add it, from a terminal

```
sudo apt-get install cheese
```

Or through add/remove programs.

I've not had any experience with skype, but in getting other Audio programs to capture the mic in Intrepid I've had to make sure that the proper mic was chosen in my audio mixer(double click on the little speaker on the taskbar)

Thanks for telling me where to find cheese, gtrtx.  Re Skype, of course it worked "right out of the box" in UNR/Hardy.  And I do recall having to surf this forum a bunch before getting it to work on my two desktops (work/home) when I upgraded to Intrepid.  I've tried a few things today but had no luck.  I'll wait and see if someone else has the same problem and gets it fixed.  In the meantime I can always reboot to Hardy if I have to use Skype (though I hate the thought of having to toggle between releases of Ubuntu).  By proper mic, do you mean "Mic" or "Front Mic"?

qednick, if only I was as clever as you about posting I would quote you too in this posting.  :)  I bet you are right, and the problem is that the card is not as good.  This is a controlled experiment: same network, same version of Ubuntu, very different results.  I was so disappointed I was beginning to consider the idea of sending it back and waiting for Amazon to stock them again, in the hope that I just got a dud.  As a last result I googled how to boost the wireless signal this morning and found a website with a template for building a parabolic antenna.  I figured, why not try, and with a leftover scrap from the metal roof that went on a part of my house last year, made an antenna.  I'll be darned if it didn't work!  That vaio now shows 85% where it used to show 30% (kitchen).  The meso couldn't keep the connection out on my deck and now it does perfectly well.  So it is not getting returned.  I still laugh out loud every time I think about it.  :D  :D

---

### Post by gtrtx on 2009-03-18
```
Which media player are you using? I'm using Rhythmbox.
``` 

I use Exaile, or Aqualung most of the time. I've never really cared for Rhythmbox.  I like Aqualung on my desktop as I've can get the best sound out of it after installing LADSPA plugins  It's really a very basic music player, nothing really fancy. I actually don't use the one from the repos, as it's always been quite buggy. I use the one from [www.getdeb.net](www.getdeb.net). 

```
By proper mic, do you mean "Mic" or "Front Mic"?
```

I suppose it depends on what Mic you are using with Skype. If it's plugged into the mic input(on the side next to the headphone input) it would be "Mic". "Front Mic" is the one built into the unit.  I know alot of folks use the USB headset with Skype, which I have no experience with. How are you using it?

I may install Skype to just to play with it.

---

### Post by qednick on 2009-03-18
> **muzincs said:**
> As a last result I googled how to boost the wireless signal this morning and found a website with a template for building a parabolic antenna.  I figured, why not try, and with a leftover scrap from the metal roof that went on a part of my house last year, made an antenna.  I'll be darned if it didn't work!  That vaio now shows 85% where it used to show 30% (kitchen).  The meso couldn't keep the connection out on my deck and now it does perfectly well.  So it is not getting returned.  I still laugh out loud every time I think about it.  :D  :D

Are you serious???!!!!?????? :eek:

I was in Office Max buying some memory sticks the other day and I got talking to one of the sales guys in the computer dept. and he said he had a HP netbook running XP. He said his wireless wasn't so hot on that either. I really just think it's an overall netbook thing. I'm not sure but I think some laptops actually use the casing as an antenna. #-o

BTW you can multi-quote by clicking on the little icon to the right of the main "quote" icon. ;-)

---

### Post by gtrtx on 2009-03-18
I just installed Skype and did a couple test calls with it. It worked pretty well. 

I did have to install it 3 times, the first two didn't work. The one that did work was from the Medibuntu repos:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After I added medibuntu to my sources I did:

```
sudo apt-get install skype-common skype-static
```

Just plain skype didn't work, gave me a lib error, so I had to use skype-static. 

I don't have a headset or a proper mic, so I just used the mic built into the netbook. I did have to set my input source(which I have 2 of, and not sure why) to "Front Mic" as well as making sure that the Recording level sliders where up(not too high or it feeds back). 

I did a couple test calls and they worked ok. I had to get close to the netbooks mic for it to be lound enough. I also called my cell phone with no issue. I only tested the camera through the config, and it seemed to be working well. 

Overall, if I had a proper Microphone, I think it would be very usable. It actually is now, other than having to stick my face in the onboard mic 

Muzincs, what errors are you getting with Skype?

---

### Post by muzincs on 2009-03-18
> **gtrtx said:**
> 
I suppose it depends on what Mic you are using with Skype. If it's plugged into the mic input(on the side next to the headphone input) it would be "Mic". "Front Mic" is the one built into the unit.  I know alot of folks use the USB headset with Skype, which I have no experience with. How are you using it?

I may install Skype to just to play with it.
I am planning on using the built in mic (less stuff to carry around, less weight).  It would be *so* great if you played with Skype and let me know what you find out.  Actually, if you don't mind, would you please post the settings you have for all things audio?  I have played with everything and I cannot record, period.  No wonder Skype does not work.

> **qednick said:**
> Are you serious???!!!!?????? :eek:

BTW you can multi-quote by clicking on the little icon to the right of the main "quote" icon. ;-)

Ah!, the joys of multi-quoting...  :)  Thanks.

Re the parabolic antenna: I am totally serious.  Is this a riot or what?  All it is is a square piece of metal (painted, actually), bent just the right amount and then stuck behind the tip of the antenna at just the right distance.  If I knew how to upload a pic, I would.  If you want the url for the template/instructions, just holler.  It works really well for me because I have the router at one end of the house (have to) so I was wasting half the signal strength on my neighbors (who cannot use it anyway (secured)).

---

### Post by qednick on 2009-03-18
I installed skype from their web site. Video works well with built-in webcam. However, I have 8 different options for the mic (5 possibles for the built-in mic). Anyways, my battery is about to run out and I'm off to bed so I'll tinker with it in the morning and post results.

> **muzincs said:**
> 
Re the parabolic antenna: I am totally serious.  Is this a riot or what?  All it is is a square piece of metal (painted, actually), bent just the right amount and then stuck behind the tip of the antenna at just the right distance.  If I knew how to upload a pic, I would.  If you want the url for the template/instructions, just holler.  It works really well for me because I have the router at one end of the house (have to) so I was wasting half the signal strength on my neighbors (who cannot use it anyway (secured)).

Honestly, I thought you were kidding LMAO. I appreciate the offer but I already went and bought another access point and set it up as a repeater which is working really well for me right now. 

I am tempted to make some kind of comment about tin foil hat antenna but... ;-)

---

### Post by muzincs on 2009-03-18
> **gtrtx said:**
> I just installed Skype and did a couple test calls with it. It worked pretty well. 

I did have to install it 3 times, the first two didn't work. The one that did work was from the Medibuntu repos:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After I added medibuntu to my sources I did:

```
sudo apt-get install skype-common skype-static
```

Just plain skype didn't work, gave me a lib error, so I had to use skype-static. 

I don't have a headset or a proper mic, so I just used the mic built into the netbook. I did have to set my input source(which I have 2 of, and not sure why) to "Front Mic" as well as making sure that the Recording level sliders where up(not too high or it feeds back). 

I did a couple test calls and they worked ok. I had to get close to the netbooks mic for it to be lound enough. I also called my cell phone with no issue. I only tested the camera through the config, and it seemed to be working well. 

Overall, if I had a proper Microphone, I think it would be very usable. It actually is now, other than having to stick my face in the onboard mic 

Muzincs, what errors are you getting with Skype?

Everything works except when I try the test call it comes back with something like "audio capture problem" or it doesn't complain but I can't hear myself.

I also have two input sources.  Did you set both of them to "Front Mic"?

I installed the package from the Skype website (both times, in UNR and Intrepid), and it installed fine right away.  Go figure.

I'll try setting both input sources to Front Mic and if that doesn't work, I'll reinstall it the way you did it.

---

### Post by gtrtx on 2009-03-18
Muzincs,

My Skype audio settings are all default so I didn't actually change anything there.

Under my Volume control under Options tab I have "Front Mic" as input source. Under the Recording tab I have the Capture Sliders pushed up just below the point of feedback. 

If these options don't appear in your audio mixer, click the preferences button at the bottom and it will let you add them. 

One last thing, you can also add, from the preferences, "Front Mic Boost" this should give you a little more in the way of mic volume.

If you have any other specific questions just let me know. I'll be up for a little bit longer, but bedtime is nearing.

---

### Post by gtrtx on 2009-03-18
> **muzincs said:**
> I'll try setting both input sources to Front Mic and if that doesn't work, I'll reinstall it the way you did it.

Both of mine are set to Front Mic.

Which one did you install from the web site? The Only version I saw stated it was for 7.04-8.04 and that one didn't work for me.

***I just checked and it appears that the static version from the repos is the current version.

---

### Post by muzincs on 2009-03-18
> **gtrtx said:**
> I don't have a headset or a proper mic, so I just used the mic built into the netbook. I did have to set my input source(which I have 2 of, and not sure why) to "Front Mic" as well as making sure that the Recording level sliders where up(not too high or it feeds back). 


gtrtx, you are a genius!  I set both input sources to Front Mic, and had to slide down the volume in capture 1 a lot (else it screeches like hell) and now Skype works!!!

So now that you have it installed do you suppose you could figure out how to get the camera to work???  (My parents and siblings who are scattered around the globe will be so thankful!)  When I test it while configuring Skype it works.  But when I call, it doesn't.  It did in Hardy.

---

### Post by muzincs on 2009-03-18
> **gtrtx said:**
> Which one did you install from the web site? The Only version I saw stated it was for 7.04-8.04 and that one didn't work for me.


That's the one I got and I think it would not install at first (in Intrepid) because of missing stuff.  Then I found some code online that basically updated Intrepid but failed to install Skype.  At that point I tried installing the same package again, and that time it worked.

---

### Post by gtrtx on 2009-03-18
Cool, glad you got that part working.:guitar:

Not sure about the camera, mine also works when testing. I don't know any other way to test it. 

I suppose I could install in on my desktop. Will Skype still allow the camera to send a picture if the other party doesn't have a camera?

---

### Post by muzincs on 2009-03-18
> **gtrtx said:**
> Cool, glad you got that part working.:guitar:

Not sure about the camera, mine also works when testing. I don't know any other way to test it. 

I suppose I could install in on my desktop. Will Skype still allow the camera to send a picture if the other party doesn't have a camera?

I think it does.

Sorry it took me a while to reply.  I got carried away fiddling with the meso and forgot I was cooking black beans.  :D

---

### Post by gtrtx on 2009-03-19
Well, it's getting pretty close to my bedtime.

Us geniuses need our rest!:wink:

But seriously, I'll play with it a bit tomorrow, I think we should be able to get it working. Probably a config setting or maybe something blocking it. :?:

I'll hollar if I find anything, and probably even if I don't. 

take care

---

### Post by muzincs on 2009-03-19
> **qednick said:**
> Honestly, I thought you were kidding LMAO. I appreciate the offer but I already went and bought another access point and set it up as a repeater which is working really well for me right now. 

I am tempted to make some kind of comment about tin foil hat antenna but... ;-)
I had seen your earlier post about the access point but I really didn't want go that route because I would have to run wires out in the open (house has no attic, weird, I know, it's very modern looking, flat roof sort of).
Then again, maybe I don't quite know how the access points work...

---

### Post by muzincs on 2009-03-19
> **gtrtx said:**
> Well, it's getting pretty close to my bedtime.

Us geniuses need our rest!:wink:

But seriously, I'll play with it a bit tomorrow, I think we should be able to get it working. Probably a config setting or maybe something blocking it. :?:

I'll hollar if I find anything, and probably even if I don't. 

take care

Great.  Thanks a bunch for fixing the audio.  I'll be checking the thread.
You take care.

---

### Post by qednick on 2009-03-19
> **muzincs said:**
> I had seen your earlier post about the access point but I really didn't want go that route because I would have to run wires out in the open (house has no attic, weird, I know, it's very modern looking, flat roof sort of).
Then again, maybe I don't quite know how the access points work...

No need for wires - you simply set up the wireless access point to "repeat" the existing signal then plug it in in the area you want the boosted signal. You do however usually need to get the same make of AP as your first wireless AP/router. I use the linksys type. Took some figuring out but works like a treat.


> **gtrtx said:**
> I have things setup this way over my local network using sshfs. Everything works quite well. I'm even streaming live TV from my desktop with a tv tuner card. 

Over the internet, however, I'm not having the same luck. I can mount shares over the internet and access my files, but not get them to play through a media player.  I just attributed it to a bandwith issue. If there is a way to overcome this I'm interested.

Just got to the office and tried it with Rhythmbox. Works perfectly. So maybe it is just some bandwidth issue?

---

### Post by gtrtx on 2009-03-19
Muzincs,

I installed Skype on my desktop. When I call it from my netbook, the camera seems to work fine. I do have to click the little blue button and choose "Start My Video"

When you choose that option, does it tell you anything at all? Also, does it show you the little camera window? 

I'm not sure what else to check....as I really didn't have to do anything to get it to work.

> **qednick said:**
> 
Just got to the office and tried it with Rhythmbox. Works perfectly. So maybe it is just some bandwidth issue?

Yes, I was checking my connection speed at work and it's pretty miserable. Also, I know the bunch of goofs that "administer" our "network" and they've got it pretty screwed up. I bet it'll work fine when If I connect to a decent network with a decent internet connection. 

I just connected to my public IP(from my home internet connection) and mounted my music directory on my desktop system with sshfs and it's working fine.

---

### Post by qednick on 2009-03-19
> **gtrtx said:**
> Yes, I was checking my connection speed at work and it's pretty miserable. Also, I know the bunch of goofs that "administer" our "network" and they've got it pretty screwed up. I bet it'll work fine when If I connect to a decent network with a decent internet connection. 

I just connected to my public IP(from my home internet connection) and mounted my music directory on my desktop system with sshfs and it's working fine.

Yup I figured it must just be the bandwidth - was the only thing that made sense.

Anyhoo... just tried plugging in a small LCD monitor I have lying around. Was like looking at the screen though wobbly jello. Anyone else noticed that issue or had success with an external monitor.
*(Edit) **UPDATE** Scratch that... I figured out what it was. Just screen resolution needed messing with. I guess it'll just look much better if used a higher res monitor. Might try it at work tomorrow.*

BTW, can't get my internal microphone to work at all since updating to 8.10 - tried Skype, Sound Recorder and Audicity.

---

### Post by gtrtx on 2009-03-19
> **qednick said:**
> 
BTW, can't get my internal microphone to work at all since updating to 8.10 - tried Skype, Sound Recorder and Audicity.

Do you have Front Mic chosen as your input source in your audio mixer? Also turn up Capture and Capture 1 in your mixer as well. 


I've used it with an external monitor. I did have to monkey around with the display settings but I got it to work and it works pretty good. 

One other thing, I was getting pretty bad tearing when watching movies and such. I found that if you use a player like VLC and change the adapter number from -1 to 1 it eliminates the tearing. I also use xine and set the adapter to overlay which does the same thing. No tearing in the video playback. The only drawback is that when you open menus or anything over the video there is a blue outline, but I can tolerate that more than tearing video.

---

### Post by muzincs on 2009-03-19
> **gtrtx said:**
> Muzincs,

I installed Skype on my desktop. When I call it from my netbook, the camera seems to work fine. I do have to click the little blue button and choose "Start My Video"

When you choose that option, does it tell you anything at all? Also, does it show you the little camera window? 


What little button?  I don't see any.
What option?  :(

---

### Post by muzincs on 2009-03-19
> **qednick said:**
> No need for wires - you simply set up the wireless access point to "repeat" the existing signal then plug it in in the area you want the boosted signal. You do however usually need to get the same make of AP as your first wireless AP/router. I use the linksys type. Took some figuring out but works like a treat.


My router is Netgear.  Do you know if a Netgear AP is especially difficult to configure?

---

### Post by gtrtx on 2009-03-19
> **muzincs said:**
> What little button?  I don't see any.
What option?  :(

After you establish a connection with the other party....theres a little blue button, click that and it gives video options

---

### Post by muzincs on 2009-03-19
> **gtrtx said:**
> After you establish a connection with the other party....theres a little blue button, click that and it gives video options
Ahhh!  You are so very clever.  I am sitting out on the deck (gorgeous Texas weather) and wasn't bothering to run back to my desktop to answer the call.

Thank you so much!!!

On another subject, I chose to live dangerously with the little meso (auto login) but network-manager wants a password to unlock the keyring before connecting to the network. A pain in the neck.  I've seen two solutions: a blank password for the keyring (too dangerous for my taste) and switching to wicd (I think that's the name).  Have you tried it?  Would you recommend it for the meso?

At this rate you and qednick are going to bill me.  :o

---

### Post by gtrtx on 2009-03-19
> **muzincs said:**
> 
On another subject, I chose to live dangerously with the little meso (auto login) but network-manager wants a password to unlock the keyring before connecting to the network. A pain in the neck.  I've seen two solutions: a blank password for the keyring (too dangerous for my taste) and switching to wicd (I think that's the name).  Have you tried it?  Would you recommend it for the meso?

That's odd, mine doesn't ask for a password unless I log on to a different network, then switch back to my network or something. It seems that it sometimes asks for it sporadically, but its always filled in and I just hit connect. Isn't there an option or checkbox to remember the password or something? I'm trying to replicate it and can't get it to ask me....I've had issues with the keyring in the past so I know how it can be a pain. Is your keyring password the same as your login?

Never used wicd, it looks neat, but network manager seems to do fine for me.


> **muzincs said:**
> 
At this rate you and qednick are going to bill me.  :o

Nah, just so long as you refer to me as a genius every so often!!!:razz:

---

### Post by qednick on 2009-03-19
> **muzincs said:**
> My router is Netgear.  Do you know if a Netgear AP is especially difficult to configure?

Not sure. Best thing to do would google your model number and "repeater" to see if you can find any instructions (from Netgear) and any posts listing any difficulties. That's basically what I did for my Linksys router and access point.

> **gtrtx said:**
> Do you have Front Mic chosen as your input source in your audio mixer? Also turn up Capture and Capture 1 in your mixer as well. 


I've used it with an external monitor. I did have to monkey around with the display settings but I got it to work and it works pretty good. 

One other thing, I was getting pretty bad tearing when watching movies and such. I found that if you use a player like VLC and change the adapter number from -1 to 1 it eliminates the tearing. I also use xine and set the adapter to overlay which does the same thing. No tearing in the video playback. The only drawback is that when you open menus or anything over the video there is a blue outline, but I can tolerate that more than tearing video.

I don't even have "Front Mic" as an option in skype. I have:

Default Device (Default)
HDA Intel (hw,Intel,0)
HDA Intel (plughw,Intel,0)
HDA Intel (hw,Intel,4)
HDA Intel (plughw,Intel,4)
hdmi
headset
pulse

In SoundRecorder, it just says "Record from Input" then "Capture" is the only option.

In Audacity preferences, I see these options for Input:
OSS /dev/dsp
ALSA HDA Intel: ALC268 Analog (hw0,0)
ALSA HDA Intel: ALC268 Analog (hw0,4)

:confused:

---

### Post by gtrtx on 2009-03-19
> **qednick said:**
> Not sure. Best thing to do would google your model number and "repeater" to see if you can find any instructions (from Netgear) and any posts listing any difficulties. That's basically what I did for my Linksys router and access point.



I don't even have "Front Mic" as an option in skype. I have:

Default Device (Default)
HDA Intel (hw,Intel,0)
HDA Intel (plughw,Intel,0)
HDA Intel (hw,Intel,4)
HDA Intel (plughw,Intel,4)
hdmi
headset
pulse

In SoundRecorder, it just says "Record from Input" then "Capture" is the only option.

In Audacity preferences, I see these options for Input:
OSS /dev/dsp
ALSA HDA Intel: ALC268 Analog (hw0,0)
ALSA HDA Intel: ALC268 Analog (hw0,4)

:confused:

The settings aren't in Skype but rather in your main audio mixer settings. In Skype just leave everything default. 

To get to your system audio mixer double click on  the speaker icon you use for your main volume. This is where you set the Front Mic under options. If it's not there click preferences and put a check in Options and it will show up.

---

### Post by muzincs on 2009-03-19
> **gtrtx said:**
> That's odd, mine doesn't ask for a password unless I log on to a different network, then switch back to my network or something. It seems that it sometimes asks for it sporadically, but its always filled in and I just hit connect.
Do you auto-login?  That seems to make all the difference.  If you log in with a password it remembers it.

> Is your keyring password the same as your login?  Sure is.

> Nah, just so long as you refer to me as a genius every so often!!!:razz:  Gosh, happy to indulge you!  :P

---

### Post by gtrtx on 2009-03-19
> **muzincs said:**
> Do you auto-login?  That seems to make all the difference.  If you log in with a password it remembers it.


No, I don't auto-login, that must be it, I suppose. In that case, not sure....

---

### Post by muzincs on 2009-03-19
> **qednick said:**
> Not sure. Best thing to do would google your model number and "repeater" to see if you can find any instructions (from Netgear) and any posts listing any difficulties. That's basically what I did for my Linksys router and access point.


Yes, that sounds like the thing to do.  I've looked a bit already.  In Amazon people are complaining that Netgear labels the bridge/APs as compatible with several models of router, but they are not!!  Shame on them.

---

### Post by muzincs on 2009-03-19
> **gtrtx said:**
> No, I don't auto-login, that must be it, I suppose. In that case, not sure....
I'll keep reading about wicd and then decide.  Apparently in some Ubuntu poll half the people prefer wicd.

---

### Post by qednick on 2009-03-19
> **gtrtx said:**
> The settings aren't in Skype but rather in your main audio mixer settings. In Skype just leave everything default. 

To get to your system audio mixer double click on  the speaker icon you use for your main volume. This is where you set the Front Mic under options. If it's not there click preferences and put a check in Options and it will show up.

Well that would explain why I couldn't find it in there then. :oops:

Anyways, I made sure it was on and moved the volume sliders up... but I still can't seem to input any sound. Either that or it's just so quiet I can barely hear it above the dishwasher in the background. Think I'll try plugging some speakers in at the office tomorrow.

---

### Post by qednick on 2009-03-20
Does anybody know what kind of RAM these things take? I'd like to try upgrading to 2GB - I know it'll likely void the warranty but I think we meso G users have already established that we like to live dangerously. :twisted:

---

### Post by gtrtx on 2009-03-20
> **qednick said:**
> Does anybody know what kind of RAM these things take? I'd like to try upgrading to 2GB - I know it'll likely void the warranty but I think we meso G users have already established that we like to live dangerously. :twisted:

It's my understanding that it does support 2GB, but the ram is not easily accessible. It most certainly would void the warranty. Not sure of the type of RAM, but I would like to upgrade mine as well. I've yet to find any information on exactly how to do it. 

I wouldn't mind a bigger HD as well. 

Maybe one day I'll get brave and dissassemble the thing. I'm quite certain I can take it apart. It's putting it back together that I'm worried about.:shock:

---

### Post by qednick on 2009-03-20
> **gtrtx said:**
> It's my understanding that it does support 2GB, but the ram is not easily accessible. It most certainly would void the warranty. Not sure of the type of RAM, but I would like to upgrade mine as well. I've yet to find any information on exactly how to do it. 

I wouldn't mind a bigger HD as well. 

Maybe one day I'll get brave and dissassemble the thing. I'm quite certain I can take it apart. It's putting it back together that I'm worried about.:shock:

Well the case looks easy to take apart. I might do it this afternoon and have a scout around - just for kicks and giggles you know. \\:D/

Not that I need the extra HD space or anything (keeping just about everything on my remote mount) but I did stick a SDHC in the side for the hell of it.

**(Edit) **UPDATE****
Just did some "exploratory surgery" on my meso. The screws came out easy and I cracked the case backing off about 1/2 inch. I lacked the testicular circumference to crack it apart any more than that for now (didn't want to dislodge any attached wires or anything). Could do with a small flashlight or something to get a better peek inside before I build up the bottle to open it further.

---

### Post by muzincs on 2009-03-20
> **qednick said:**
> Well the case looks easy to take apart. I might do it this afternoon and have a scout around - just for kicks and giggles you know. \\:D/

Not that I need the extra HD space or anything (keeping just about everything on my remote mount) but I did stick a SDHC in the side for the hell of it.

**(Edit) **UPDATE****
Just did some "exploratory surgery" on my meso. The screws came out easy and I cracked the case backing off about 1/2 inch. I lacked the testicular circumference to crack it apart any more than that for now (didn't want to dislodge any attached wires or anything). Could do with a small flashlight or something to get a better peek inside before I build up the bottle to open it further.

The meso is made by AMtek SYSTEM CO., from Taiwan.  In their line up the meso is the LC89 and it comes in two versions.  The other one has 2G/160G.
Check it out at [http://www.amtek.com.tw/english/LC89_spec-2.htm](http://www.amtek.com.tw/english/LC89_spec-2.htm)

---

### Post by gtrtx on 2009-03-20
> **qednick said:**
> Well the case looks easy to take apart. I might do it this afternoon and have a scout around - just for kicks and giggles you know. \\:D/

Not that I need the extra HD space or anything (keeping just about everything on my remote mount) but I did stick a SDHC in the side for the hell of it.

**(Edit) **UPDATE****
Just did some "exploratory surgery" on my meso. The screws came out easy and I cracked the case backing off about 1/2 inch. I lacked the testicular circumference to crack it apart any more than that for now (didn't want to dislodge any attached wires or anything). Could do with a small flashlight or something to get a better peek inside before I build up the bottle to open it further.

I've searched the web trying to find information regarding this but can't find anything specific for the Sylvania. I've found a couple for different netbooks and they look pretty straight forward.

Oh, and I got the sshfs to work from my job. Music seems to work pretty well, videos are a no go. I've heard we're going to upgrade our connection so that should help when that happens.

---

### Post by qednick on 2009-03-20
> **gtrtx said:**
> I've searched the web trying to find information regarding this but can't find anything specific for the Sylvania. I've found a couple for different netbooks and they look pretty straight forward.

Oh, and I got the sshfs to work from my job. Music seems to work pretty well, videos are a no go. I've heard we're going to upgrade our connection so that should help when that happens.

Cool. Haven't tried the video myself yet though. Does seem to copy large files pretty well though. I'm getting consistent download speeds of about 400-500K/sec both at the office and now at home since putting the repeater in.

---

### Post by the3dman on 2009-03-24
I have put a picture guide to replacing the memory and the hard drive on the Meso on my Meso site. Just follow the link in my signature.

Enjoy

---

### Post by gtrtx on 2009-03-24
> **the3dman said:**
> I have put a picture guide to replacing the memory and the hard drive on the Meso on my Meso site. Just follow the link in my signature.

Enjoy

Excellent! You DA MAN!!!

Is it correct that the Meso will upgrade to 2GB of RAM?

What are the exact specs of the memory that is uses?

it should work?

---

### Post by qednick on 2009-03-24
> **the3dman said:**
> I have put a picture guide to replacing the memory and the hard drive on the Meso on my Meso site. Just follow the link in my signature.

Enjoy

You are my hero!!!! :guitar:

Quick question though...

Does it take 2 ram modules (2 x 1GB each) or should I get a single 2GB stick and replace the one that's already there?

Also, what kind of module does it take? I couldn't find the Meso listed on any memory sites.


> **muzincs said:**
> The meso is made by AMtek SYSTEM CO., from Taiwan.  In their line up the meso is the LC89 and it comes in two versions.  The other one has 2G/160G.
Check it out at [http://www.amtek.com.tw/english/LC89_spec-2.htm](http://www.amtek.com.tw/english/LC89_spec-2.htm)

Wow. Totally missed this post for some strange reason. Unfortunately it takes forever to get their site to load. :-(

---

### Post by the3dman on 2009-03-24
There is only 1 slot for a chip, so you will need a 2gb chip which is the max. As far as what kind, I think it is DDR2 but I am not 100% sure the memory in there didn't say much on it. I will do some more research though and update you guys as I find out more.

---

### Post by qednick on 2009-03-25
> **the3dman said:**
> There is only 1 slot for a chip, so you will need a 2gb chip which is the max. As far as what kind, I think it is DDR2 but I am not 100% sure the memory in there didn't say much on it. I will do some more research though and update you guys as I find out more.

Awesome!!

---

### Post by greyfox1 on 2009-03-27
Add me to the list of people who got wifi working by installing Intrepid.  Kinda stinks to give up the lpia kernel and a bit of battery life, but the unit is at least usable now.  Thank goodness!

Hopefully once Jaunty hits, this problem will be resolved and I can go to Jaunty Netbook Remix.

---

### Post by Veal_Calf on 2009-03-28
Got my Snow Meso from Amazon (last one in stock) on Thursday. This thread has been very helpful with the few tiny problems I've had. I've now gotten the webcam working with Cheese (it was the fn+esc being toggled off). I still have not gotten the bios update to work though. Every time I try to run the update, it will ask me for my password, and immediately quit. Overall its a great little netbook and is a great value.

---

### Post by qednick on 2009-03-28
> **Veal_Calf said:**
> Got my Snow Meso from Amazon (last one in stock) on Thursday. This thread has been very helpful with the few tiny problems I've had. I've now gotten the webcam working with Cheese (it was the fn+esc being toggled off). I still have not gotten the bios update to work though. Every time I try to run the update, it will ask me for my password, and immediately quit. Overall its a great little netbook and is a great value.

Congrats on the purchase!! Have you installed anything prior to running the bios update?

---

### Post by Veal_Calf on 2009-03-29
I had but then I did a recovery and still no luck. Also after resume, I have no sound.

---

### Post by mwdowns on 2009-03-30
Gah!  I'm so jealous of you folks who've got your G Mesos already.  I put in an order for a yellow one at Amazon over a month ago and it still hasn't come in.  :(  Hopefully soon.

---

### Post by qednick on 2009-03-30
> **mwdowns said:**
> Gah!  I'm so jealous of you folks who've got your G Mesos already.  I put in an order for a yellow one at Amazon over a month ago and it still hasn't come in.  :(  Hopefully soon.

I was in same boat but gave up on Amazon, canceled the order and found one at MacMall.com for immediate shipment.

---

### Post by the3dman on 2009-03-30
> **Veal_Calf said:**
> Got my Snow Meso from Amazon (last one in stock) on Thursday. This thread has been very helpful with the few tiny problems I've had. I've now gotten the webcam working with Cheese (it was the fn+esc being toggled off). I still have not gotten the bios update to work though. Every time I try to run the update, it will ask me for my password, and immediately quit. Overall its a great little netbook and is a great value.

The Bios Update seems to only work on a fresh install with nothing extra added, updated or installed. Try doing a factory restore to stock then installing it. If you already tried that with no luck (which it appears you have), try re downloading the bios update and trying it again. Maybe it got corrupted while downloading.

---

### Post by Mokele on 2009-03-31
So did anybody find what kind of memory I could buy for upgrade?

---

### Post by Veal_Calf on 2009-03-31
> **Mokele said:**
> So did anybody find what kind of memory I could buy for upgrade?

I'm not entirely sure what kind of memory it uses, but here is the detailed spec page of the original manufacturer (translated of course) [http://translate.google.com/translate?u=http%3A%2F%2Fwww.amtek.com.tw%2Fenglish%2FLC89_spec-2.htm&sl=zh-CN&tl=en&hl=en&ie=UTF-8](http://translate.google.com/translate?u=http%3A%2F%2Fwww.amtek.com.tw%2Fenglish%2FLC89_spec-2.htm&sl=zh-CN&tl=en&hl=en&ie=UTF-8)

Then there is the3dman's pictures of the inside of his meso [http://forum.lowpowertech.com/viewtopic.php?f=6&t=10&sid=96f6e2fd679eeebfb97ce02d8490b07b](http://forum.lowpowertech.com/viewtopic.php?f=6&t=10&sid=96f6e2fd679eeebfb97ce02d8490b07b)

Personally I'm good with the memory for now, but maybe in a few months I will think about upgrading.

---

### Post by Mokele on 2009-04-01
Well, I was going to open it anyway: I need to clean the keyboard - my wife has spilled a bit of sweet juice in there, so some keys got sticky. I hate  doing it due to my poor close vision, but it will rather be me than her ;). Since the memory is cheap these days I would prefer not to repeat the procedure again and upgrade it as well. My concern is the memory voltage (2.5V or 1.8V). Where else I can f... up? Its 2GB SODIMM DDR2 667mhz chip, according to chinese specs, no more info... I guess its PC2 5300. Or 5400? Or (worse) 4200?

---

### Post by keeptrying1188 on 2009-04-01
I followed the3dman's instructions opening the G-Meso. I ordered the 'Crucial 2gb DDR2 5200' RAM chip from Amazon.com for under $19 and replaced the original 1gb chip with the new 2gb chip. The G-Meso was re-assembled and i had to repeat the de-assembling and re-assembling a couple of times as my keyboard did not work--the ribbon wasn't locked properly. Finally it worked and the RAM registered at 2gb!!! Everything is running very fast. The fan does not come on as often now which i'm happy with. I regret though: i lost one of the stainless steel screws!? So, be very cautious with them when you remove them.

Thank you the3dman! You're a gem!

---

### Post by keeptrying1188 on 2009-04-01
I made an error describing the 2gb RAM chip: it is 2GB 200PIN DDR2 SODIMM 5300 made by CRUCIAL.

---

### Post by qednick on 2009-04-01
> **keeptrying1188 said:**
> I made an error describing the 2gb RAM chip: it is 2GB 200PIN DDR2 SODIMM 5300 made by CRUCIAL.

Splendiferously awesome!! Going to order me a chippie now!! 
\\:D/

*EDIT*
Looking now and there's different ones - do you know the model number or have a link?

---

### Post by keeptrying1188 on 2009-04-02
> **qednick said:**
> Splendiferously awesome!! Going to order me a chippie now!! 
\\:D/

*EDIT*
Looking now and there's different ones - do you know the model number or have a link?
This is the link:

[http://www.amazon.com/gp/product/B000F7QRTG](http://www.amazon.com/gp/product/B000F7QRTG)

Good Luck.

---

### Post by qednick on 2009-04-02
> **keeptrying1188 said:**
> This is the link:

[http://www.amazon.com/gp/product/B000F7QRTG](http://www.amazon.com/gp/product/B000F7QRTG)

Good Luck.

FANTASTIC!! THANKS!!

I should have it in a few days. I'll post my experience here once it's fitted.

---

### Post by the3dman on 2009-04-05
I am glad to see the progress on the memory upgrade. Thanks for the info on the type of ram. I have not had much more time to look into the type, but I am glad you figured it out. Very Nice work!!

---

### Post by gtrtx on 2009-04-06
Very cool info regarding the memory. Looks like I'll be upgrading soon as well. May also look at upgrading the hard drive. 

I also wanted to share that I've installed the latest daily 9.04 lpia port.

[http://cdimage.ubuntu.com/ports/daily/current/]("http://cdimage.ubuntu.com/ports/daily/current/")

It works pretty well, installs without issue and seems to perform pretty well. Unfortunately I really don't see too much benefit over the i386 version. Battery life is about the same, and there doesn't appear to be much performance gain(maybe just a bit, could be my imagination).  Suspend also doesn't work out of the box but the fix/workaround that was posted several pages back(for Intrepid) does still work. 

Of course it is still beta and the they are nearing the final release in a couple weeks so there are alot of updates. Several a day.

I also know that they are making a concerted effort in getting suspend/hybernation to work on a wider variety of systems, so the workaround may get in the way. I remove every so often ater updates to test it(actually, only if a relevent component is updated).   

Anyways, just wanted to share......

---

### Post by qednick on 2009-04-07
> **gtrtx said:**
> Very cool info regarding the memory. Looks like I'll be upgrading soon as well. May also look at upgrading the hard drive. 

I also wanted to share that I've installed the latest daily 9.04 lpia port.

[http://cdimage.ubuntu.com/ports/daily/current/]("http://cdimage.ubuntu.com/ports/daily/current/")

It works pretty well, installs without issue and seems to perform pretty well. Unfortunately I really don't see too much benefit over the i386 version. Battery life is about the same, and there doesn't appear to be much performance gain(maybe just a bit, could be my imagination).  Suspend also doesn't work out of the box but the fix/workaround that was posted several pages back(for Intrepid) does still work. 

Of course it is still beta and the they are nearing the final release in a couple weeks so there are alot of updates. Several a day.

I also know that they are making a concerted effort in getting suspend/hybernation to work on a wider variety of systems, so the workaround may get in the way. I remove every so often ater updates to test it(actually, only if a relevent component is updated).   

Anyways, just wanted to share......

Thanks for the info! I think I'll wait a couple of weeks to see if things are improved on that score.

On another note... I have my RAM but haven't had a spare 30 minutes to try and fit it. I'm still planning on posting my results here though once I do.

---

### Post by qednick on 2009-04-11
Well I finally got round to installing my RAM.

Many thanks to the3dman and keeptrying1188 for all the info. Here's a couple of notes on the experience...

To pop off the top plate (the narrow piece that surrounds the power button, I did have to take out the three retaining screws from underneath.

I couldn't figure out how to disconnect the keyboard ribbon cable and didn't want to risk harming it, so I left it connected while I replaced the RAM module.

After putting everything back together, I noticed that the same narrow top plate wouldn't seem to seat perfectly back in place - don't know why - but it's almost there and I'm not going to worry about it.

Otherwise I fired up my Meso and hey presto I now have 2GB of RAM. Yippee.

---

### Post by gnix on 2009-04-14
FYI - I just received my (refurbished) Sylvania G Meso (I found one at an online store called RCS Experience via Amazon that could ship immediately).  

I love it.  I've had it for ~1 day and so far everything is exactly what I'd hoped.  It's tiny, silent, and feather-light and the screen is surprisingly sharp and bright.  The keyboard IS extremely small, but I was expecting that.  It came with Ubuntu 8.04 and so-far no problems except for a small glitch in Compiz that I can't figure out.  The webcam and wireless worked out of the box.  The touchpad buttons ARE a little loud, but the touchpad allows tap-clicking (which I love) so no button-presses are required.

I'm happy to have it and it will be a fun toy, but one of my main reasons for buying it was to have a cheap way to try out Linux.  After this experience I think I'll feel comfortable enough to install it on a desktop at home (not at work, yet) for nearly everything.  Also FYI this would be an awesome laptop for traveling and giving presentations since it would easily fit in a purse or small backpack.  I haven't tried to hook it up to a projector yet, but mirroring the display on an external monitor was easy so it shouldn't be too hard.

My feeling is that cheapo little netbooks like this will (hopefully) help a lot of people try linux who, like me, were curious about linux but not willing to make a large investment to try it.  For $250 what's the worst that could happen?

A++

---

### Post by qednick on 2009-04-14
> **gnix said:**
> FYI - I just received my (refurbished) Sylvania G Meso (I found one at an online store called RCS Experience via Amazon that could ship immediately).  

I love it.  I've had it for ~1 day and so far everything is exactly what I'd hoped.  It's tiny, silent, and feather-light and the screen is surprisingly sharp and bright.  The keyboard IS extremely small, but I was expecting that.  It came with Ubuntu 8.04 and so-far no problems except for a small glitch in Compiz that I can't figure out.  The webcam and wireless worked out of the box.  The touchpad buttons ARE a little loud, but the touchpad allows tap-clicking (which I love) so no button-presses are required.

I'm happy to have it and it will be a fun toy, but one of my main reasons for buying it was to have a cheap way to try out Linux.  After this experience I think I'll feel comfortable enough to install it on a desktop at home (not at work, yet) for nearly everything.  Also FYI this would be an awesome laptop for traveling and giving presentations since it would easily fit in a purse or small backpack.  I haven't tried to hook it up to a projector yet, but mirroring the display on an external monitor was easy so it shouldn't be too hard.

My feeling is that cheapo little netbooks like this will (hopefully) help a lot of people try linux who, like me, were curious about linux but not willing to make a large investment to try it.  For $250 what's the worst that could happen?

A++

Congrats and welcome to the clan!!

---

### Post by cfastner on 2009-04-16
I am waiting for my Solar Sylvania Meso that I ordered from Amazon (supposed to be in SOON) but I just noticed that "www.sylvaniacomputers.com" disappeared!  

Anyone know if there is an issue with the company?  (Maybe I'll NEVER get it!) :( 

Charlie
  ~~~

---

### Post by qednick on 2009-04-16
> **cfastner said:**
> I am waiting for my Solar Sylvania Meso that I ordered from Amazon (supposed to be in SOON) but I just noticed that "www.sylvaniacomputers.com" disappeared!  

Anyone know if there is an issue with the company?  (Maybe I'll NEVER get it!) :( 

Charlie
  ~~~

Looks like it's just a web site issue. I gave up on Amazon and ended up canceling my order and buying from MacMall instead. However, the G Mesos seem to be as rare as rocking horse poop lately so not sure if MacMall or anyone else will have any left in stock. Good luck!

---

### Post by gnix on 2009-04-18
I`m having a frustrating problem with Compiz on my Meso:

When I restore (aka unmaximize) a maximized window, it *sometimes* ends up half-off the screen such that I can't see/grab the title-bar or buttons. I have to right-click and then select 'maximize' or something to get it back. I've already tried un-checking 'constrain Y' and 'snap invert' and several other things. Any ideas on how to fix this? I love the compiz effects and would like to keep them, but this is a deal-breaker if I can't fix it.

I posted this question to the `Desktop and Effects` section of UbuntuForums but go no reply so I`m thinking this might be specific to the small screen-size of netbooks.  Anybody else have any trouble with Compiz?

Thanks very much for your wisdom!!!

---

### Post by the3dman on 2009-04-21
> **gnix said:**
> I`m having a frustrating problem with Compiz on my Meso:

When I restore (aka unmaximize) a maximized window, it *sometimes* ends up half-off the screen such that I can't see/grab the title-bar or buttons. I have to right-click and then select 'maximize' or something to get it back. I've already tried un-checking 'constrain Y' and 'snap invert' and several other things. Any ideas on how to fix this? I love the compiz effects and would like to keep them, but this is a deal-breaker if I can't fix it.

I posted this question to the `Desktop and Effects` section of UbuntuForums but go no reply so I`m thinking this might be specific to the small screen-size of netbooks.  Anybody else have any trouble with Compiz?

Thanks very much for your wisdom!!!

Really not to much with experience with compiz, but I have heard of others having lots of problems with it on netbooks because of the small screen.

---

### Post by the3dman on 2009-04-21
Is anyone else having trouble accessing [www.sylvaniacomputers.com](www.sylvaniacomputers.com) or is it just me? I have not been able to open it for a week now.

---

### Post by qednick on 2009-04-21
> **the3dman said:**
> Is anyone else having trouble accessing [www.sylvaniacomputers.com](www.sylvaniacomputers.com) or is it just me? I have not been able to open it for a week now.

Yup it's been down since reported a few days ago. I hope this company hasn't gone down with the economy because they're definitely onto a winner with these machines. I'd assumed they were in short supply because they couldn't make them fast enough.

---

### Post by cfastner on 2009-04-21
I just got an email from Christa at Levin Consulting, part of the Sale Team with the following:

"I do have some information on the site. Go to [www.digitalgadgets.com](www.digitalgadgets.com)

We changed hosting companies and it is taking longer to switch over addresses with the Sylvania domain name since Sylvania is the parent company of so many products.

We hope to have it done this week, some one earlier today told me they could access it, but I still can't.* But the digitalgadets.com works right now."

---

### Post by qednick on 2009-04-21
> **cfastner said:**
> I just got an email from Christa at Levin Consulting, part of the Sale Team with the following:

"I do have some information on the site. Go to [www.digitalgadgets.com](www.digitalgadgets.com)

We changed hosting companies and it is taking longer to switch over addresses with the Sylvania domain name since Sylvania is the parent company of so many products.

We hope to have it done this week, some one earlier today told me they could access it, but I still can't.* But the digitalgadets.com works right now."

\\:D/ phew

---

### Post by the3dman on 2009-04-23
Well the netbook remix 9.04 is officially out, and it appears to be working great with exception of the standby feature (which didn't work in the Alpha or RC either), I will have to do the work around for that. But other wise it is fast and everything else is working for me. Anyone else try it yet and have a different experience?

---

### Post by qednick on 2009-04-24
> **the3dman said:**
> Well the netbook remix 9.04 is officially out, and it appears to be working great with exception of the standby feature (which didn't work in the Alpha or RC either), I will have to do the work around for that. But other wise it is fast and everything else is working for me. Anyone else try it yet and have a different experience?

Haven't tried it yet but will. Out of town until Sunday afternoon so will download the updates then. This is my first travel experience with the meso! Just loving this thing!

---

### Post by gandhii on 2009-04-25
What's "Stand-By"?    Are you meaning "Suspend" mode?

At any rate, I plan on giving 9.04 a try this weekend.  I also noticed that the meso is not mentioned in the 9.04 UNR compatibility list...  rather ironic considering the meso actually comes with UNR unlike many of those mentioned that don't.

---

### Post by gnix on 2009-04-26
This is not going to win me any points on this forum, but I want to know what people think:  I just set-up a dual boot on my Meso so it now runs Windows XP and Ubuntu 9.04 and, to my surprise, I noticed that XP is actually a bit faster than Ubuntu.  I notice it especially with things like YouTube and the webcam, but it is very noticeable, especially with multiple youtube tabs open or the like.  It also boots faster.  This has basically been my first experience with desktop Linux and one of the main advantages I was expecting was speed (for a system with relatively low-end hardware like a netbook).  I also know from experience that Windows doesn't stay fast for long and usually gets bogged down with cruft in the months following a clean install, but still... is this to be expected?  Do people in the Ubuntu community acknowledge this or is my experience singular?

---

### Post by the3dman on 2009-04-27
> **gnix said:**
> This is not going to win me any points on this forum, but I want to know what people think:  I just set-up a dual boot on my Meso so it now runs Windows XP and Ubuntu 9.04 and, to my surprise, I noticed that XP is actually a bit faster than Ubuntu.  I notice it especially with things like YouTube and the webcam, but it is very noticeable, especially with multiple youtube tabs open or the like.  It also boots faster.  This has basically been my first experience with desktop Linux and one of the main advantages I was expecting was speed (for a system with relatively low-end hardware like a netbook).  I also know from experience that Windows doesn't stay fast for long and usually gets bogged down with cruft in the months following a clean install, but still... is this to be expected?  Do people in the Ubuntu community acknowledge this or is my experience singular?

I have nothing against people who use windows, I just choose not to. I use ubuntu because number one it is free and I am cheap, number two like you said windows starts off fast the gets slow quickly, so although ubuntu may run slightly slower or boot slower, the speed never changes, it always runs smooth for me. Number three is that there are too many viruses and other spyware on the internet, so on my netbook which is mainly used for surfing the internet I prefer to have the more secure OS. But like I said "to each their own". If you like windows I won't hold anything against you for that. The more info on the meso that is posted on this thread, the better it will be, whether it be for ubuntu or windows. Knowledge is power. So thanks for your post. "Bet you didn't see that one comming."

---

### Post by the3dman on 2009-04-27
> **gandhii said:**
> What's "Stand-By"?    Are you meaning "Suspend" mode?

At any rate, I plan on giving 9.04 a try this weekend.  I also noticed that the meso is not mentioned in the 9.04 UNR compatibility list...  rather ironic considering the meso actually comes with UNR unlike many of those mentioned that don't.

Yes I did mean Suspend. "Stand-By" comes from my years of growing up with windows.

---

### Post by the3dman on 2009-04-27
Well after installing and using 9.04 since its release, I love it. After fixing the suspend issue solved by gtrtx, everything is running smooth, the only other bug I found so far is that anything I download to my desktop dosn't appear on the desktop. I have to go to places -> desktop and open the desktop folder to view the files saved to the desktop. I will look into this more later and see if I can find a fix. But other than that, it has all been clear sailing so far. 9.04 is a winner in my book.

---

### Post by qednick on 2009-04-27
> **gnix said:**
> This is not going to win me any points on this forum, but I want to know what people think:  I just set-up a dual boot on my Meso so it now runs Windows XP and Ubuntu 9.04 and, to my surprise, I noticed that XP is actually a bit faster than Ubuntu.  I notice it especially with things like YouTube and the webcam, but it is very noticeable, especially with multiple youtube tabs open or the like.  It also boots faster.  This has basically been my first experience with desktop Linux and one of the main advantages I was expecting was speed (for a system with relatively low-end hardware like a netbook).  I also know from experience that Windows doesn't stay fast for long and usually gets bogged down with cruft in the months following a clean install, but still... is this to be expected?  Do people in the Ubuntu community acknowledge this or is my experience singular?

There's pros and cons to every system. This applies even between different distros of Linux. If you find there are more pros for you to use Windows then I can't see why you shouldn't use it. Personally, I prefer either Linux or OSX over Windows any day - even if it's just because I don't feel the need to install tons of anti-malware software - which, of course, slows the system down to a crawl anyway.

I believe Ubuntu takes longer to boot up than other distros because there's a bit more eye candy and other stuff included by default - this is to make it more user friendly. However, I also believe you can turn off things you don't need so it boots faster - though I've yet to try messing with that yet.

---

### Post by the3dman on 2009-04-29
> **the3dman said:**
> Well after installing and using 9.04 since its release, I love it. After fixing the suspend issue solved by gtrtx, everything is running smooth, the only other bug I found so far is that anything I download to my desktop dosn't appear on the desktop. I have to go to places -> desktop and open the desktop folder to view the files saved to the desktop. I will look into this more later and see if I can find a fix. But other than that, it has all been clear sailing so far. 9.04 is a winner in my book.

The desktop issue was solved by switching back to remix mode then again switching back to classic mode. The problem seems to have permanently corrected itself.

---

### Post by Mokele on 2009-05-03
Successfully upgraded the memory to 2Gb following the instructions. Two notes, though:
1) I was unable to locate the lever that releases keyboard band, so I have done everything with keyboard still attached.
2) As it was mentioned before, the narrow plate in front of keyboard remains slightly popped up no matter how accurate (and strong) I was. I don't care however.
Everything works fine, but I switched to classic view similar too my desktop so it is easier to find things.

---

### Post by gtrtx on 2009-05-04
I haven't checked this thread in a while so I wanted to chime in regarding 9.04.

I've been using the lpia version since beta and have brought it current with updates. It seems to work very well. Unfortunately, I really don't see the benefit of the lpia kernel. I may be able to squeeze just a bit more battery life out of the netbook, and there may slight performance gain. But I really can't say for sure. The overall performance is better than previous versions.

The only issue is suspend doesn't seem to work out of the box, but as noted  earlier, the same fix for 8.10 seems to work. Every once in a while it won't, but the majority of the time, no issues. 

My final verdict is that I would recommend it for anybody using this netbook.

---

### Post by muzincs on 2009-05-05
Hello everyone.  I've been off the radar for a while too (tons of work).  I installed jaunty lpia (downloaded alternate iso and created a usb flash drive to install (in a jaunty laptop because apparently it won't work otherwise)).  Works like a charm, except UNR is a total mess: gnome panel disappears, firefox is in a tiny window, etc.  You better stick to the classic desktop for the time being.  My impression is that battery life is noticeably better.

There is a very good website for ubuntu on the Dell mini; lots of the tips apply to the meso too.

I agree that it is disappointing that canonical seems to be unaware that the meso exists.  Hell, I bought it because it is "ubuntu certified"!  I even left the sticker on it whereas I've always removed the windows sticker first thing.  Maybe the meso is not for sale in London(?).  Should we start an email campaign to canonical asking them to list the meso where it belongs?   :P

---

### Post by shelby_vn on 2009-05-05
You are correct this netbook rocks! I could not get Camorama working either. I got the same error. Other than that this thing works great! One thing I am not able to do, that I would like to do is upgrade to 8.10 but it wont seem to let me. In software sources under updates I set it to normal releases but it still says no updates available. Any Ideas?

---

### Post by the3dman on 2009-05-09
> **shelby_vn said:**
> You are correct this netbook rocks! I could not get Camorama working either. I got the same error. Other than that this thing works great! One thing I am not able to do, that I would like to do is upgrade to 8.10 but it wont seem to let me. In software sources under updates I set it to normal releases but it still says no updates available. Any Ideas?

You cannot upgrade from the 8.04 lpia netbook remix to the non-lpia 8.10 you must do a fresh install. Same with going from 8.04 lpia to 9.04.

---

### Post by gandhii on 2009-05-10
So...  how do we turn off Wifi?
The Fn+F4 button combo doesn't seem to do the trick.

---

### Post by the3dman on 2009-05-11
> **gandhii said:**
> So...  how do we turn off Wifi?
The Fn+F4 button combo doesn't seem to do the trick.

The long way is to right click on the network manager icon on the top right in classic desktop mode and uncheck enable wireless.

---

### Post by gandhii on 2009-05-12
Is there not a way when in normal netbook mode?

errr.   ignore me.   i did a shoddy job of reading your answer and didn't completely understand it.

---

### Post by cfastner on 2009-05-13
I am finally posting this message on a real honest to gosh Sylvania G Meso!  I have had a Meso on order with Amazon for a month and a half.  I finally found a reconditioned Solar from RCS on eBay.  I love it!  I have read all of this thread and have seen many posts about the wireless issues.  I am having an issue with WPA on my home wireless.  I know that many have upgraded to get this to work.  My biggest question is if I update to Jaunty, do I want to update to the Netbook Remix or the LPIA?

):P

Thanks for any help you can supply!

Charlie
  ~~~

---

### Post by gtrtx on 2009-05-13
I'm using the LPIA, I think that there is some performance improvement and others have said they feel the battery life is better. 

I've used the Remix interface and really don't care for it. So the LPIA w/ standard Desktop works great for me. If you've grown accustomed to the Remix interface you may want to stick with it.

So I guess you need to weigh the pros and cons between the different available versions that choose the one that will best suit your needs. 

> **cfastner said:**
> I am finally posting this message on a real honest to gosh Sylvania G Meso!  I have had a Meso on order with Amazon for a month and a half.  I finally found a reconditioned Solar from RCS on eBay.  I love it!  I have read all of this thread and have seen many posts about the wireless issues.  I am having an issue with WPA on my home wireless.  I know that many have upgraded to get this to work.  My biggest question is if I update to Jaunty, do I want to update to the Netbook Remix or the LPIA?

):P

Thanks for any help you can supply!

Charlie
  ~~~

---

### Post by the3dman on 2009-05-22
Netbook Remix and LPIA are the same. Netbook remix uses the lpia kernel instead of the regular i386. I would stick with the lpia netbook remix and just use it in standard desktop mode.

---

### Post by keeptrying1188 on 2009-05-22
I have the img file of the recent UNR 9.04 downloaded. How do I install it on my existing UNR 8.04? I do not have Windows OS as I use mac os x. Please help. I do have a USB stick or SD card with 8gb. I am really new to this and would be most appreciative for instructions. Thanks.

---

### Post by keeptrying1188 on 2009-05-22
I was able to install the UNR 9.04. @ 1st the wifi didn't work but after a few reboots i got it going. What i wonder is what should i select in the packages in Synaptic Package Manager!? What would you recommend? What should I deselect? I don't do any programming only the basic surfing on the internet, e-mail, games, wordprocessing, spreadsheet, etc.

Hope to get some advice. Thanks.

---

### Post by gandhii on 2009-05-24
I'd just go through the list or read reviews online and try thinks you think might be interesting. The general rule of thumb is to only install 1 or two things at a time, try them out and then see how things go before uninstalling it if you didn't like it or moving on and installing something else.
> **keeptrying1188 said:**
> I was able to install the UNR 9.04. @ 1st the wifi didn't work but after a few reboots i got it going. What i wonder is what should i select in the packages in Synaptic Package Manager!? What would you recommend? What should I deselect? I don't do any programming only the basic surfing on the internet, e-mail, games, wordprocessing, spreadsheet, etc.

Hope to get some advice. Thanks.

---

### Post by gandhii on 2009-05-24
OK..   I got it now.  Give me a moment, and I'll write something up.

[I]Allright.  I've read over the posts .. etc.  and I don't think I am grasping what exactly I need to do to for the suspend fix after installing 9.04.
What is the filename suppose to be for that script file?  using the name given of another wifi chip doesn't make sense.  Do I need to edit another config file somewhere to reference this script file that I am adding?[/I]

---

### Post by gandhii on 2009-05-25
Download this script file ([ATTACH]115077[/ATTACH]) to your Desktop and run the following commands in order.

This command will copy the file to /etc/pm/sleep.d and rename it to remove the extension 'sh' which was required so I could attach it to this post.
```
sudo cp ~/Desktop/rt73usb.sh /etc/pm/sleep.d/rt73usb
```

This command will give the file the permissions to execute.
```
sudo chmod 777 /etc/pm/sleep.d/rt73usb
```

Now try to suspend and see if it works.  If not.  Start over and try again, cause it worked for me, and I don't know what else to say about it.

---

### Post by gandhii on 2009-06-20
Man..  this thread has been a little dead as of late.

One problem that has been bugging me since upgrading to 9.04 is that I can no longer Alt-Tab to the ume-launcher.  It just doesn't come up as an option when alt-tabbing.  Any ideas on a fix?

---

### Post by the3dman on 2009-06-21
> **gandhii said:**
> Man..  this thread has been a little dead as of late.

One problem that has been bugging me since upgrading to 9.04 is that I can no longer Alt-Tab to the ume-launcher.  It just doesn't come up as an option when alt-tabbing.  Any ideas on a fix?

Same issue here, and I have had no luck figuring out a fix yet. I will keep trying. This has been dead here for a while.

---

### Post by rick71 on 2009-06-21
... a different issue...
Does anyone know how to get gsynaptics to work? I keep getting the "can't initialize" error. I have already added the SHMConfig = 'true', and the Input Device = "Synaptics Touchpad" lines to xorg.conf.

---

### Post by jackmg on 2009-06-21
I inadvertently was fiddling in Other Menus/Screen and Graphics Preferences while trying to get a screen grab apps to work. I think that was the last thing I did. Anyway, when I booted the netybook later on, a message windows appears before bootup finished saying that the computer was set for low resolution and I could manually configure it. I tr4ied auto detect and actually selecting the Intel 945 selection to no avail. The system is locked in 800 X 600. The screen resolution menu option does not let me change it. Returning to the Screen and Graphics Preferences menu choice is the same as the manual configuration when I boot ujp. Also, the boot sequence is now different. I had the Netbook set for siletn boot so I didntt have to enter user name and password. Now I see the reuqeist for this information display on the scroll as all the commands scroll by during boot up. It even stops and asks for the log on info. Sometimes it accepts a enter key; other times it goes to # prompt. Any ideas how aI can reverse or fix this messed up netbook.

I accessed the recovery partition but do not see any way to reinstall. Is their a way to recover to go back to the default graphic settings? 

I was also thinking about starting over with 9.04. Will this undue the locked screen resolution.

Thanks for any suggestions.

---

### Post by biyouboogie on 2009-06-26
I bought this Meso g for a friend of mine.   The system update icon appeared, and as I instructed her to do, she launched the update.   However, she had failed to plug in the A/C and the battery went dead before the update completely finished.  She plugged in the A/C and rebooted.  Now, the darn thing boots Ubuntu, and once she logs in she gets a white screen.   

I was able to use the OPTIONS menu and boot into the Gnome login screen.  Once I get logged in, I get he pretty Ubuntu background, and NOTHING ELSE.  Well, the date and time do display, and the calendar works (WOO HOO) but nothing else.  The special lpia kernel menus do not display at all.

Any suggestions?   Is the Recovery partition safe to use to restore this thing?  I think she can live with what ever files she has saved being lost.   If so, HOW???   I do not know how to get the Recovery partition to boot.  I disabled quick boot and quiet boot in the bios. 

Also, I used my USB flash drive to boot into Ubuntu Ultimate Edition 2.0 which I just happened to have LIVE on a flash drive.
I am more use to the normal screen than I am on the lpia kernel.
She is ONLY use to the lpia menus.  I am reluctant to upgrade this to Ubuntu UE for fear that battery life may not be good (after reading on someone's post) and it may be too dificult for her to understand.  She's not very computer literate, and a sudden change of screens may throw her for a loop.  :(

Any suggestions on how to use the Recovery partition, or on how to get my hands on the Installation Image would be greatly appreciated.  Better yet, how do I get this thing to boot the previous kernel.  There is no GRUB menu, so I have no options during bootup.  

I have 2 vmlinuz images.  

#1   vmlinuz-2.6.24-19-lpia
#2   vmlinuz-2.6.24-24-lpia



biyouboogie

---

### Post by biyouboogie on 2009-06-26
Well, I guess I jumped the gun a little.  I was able to modify the menu.lst on the 77.5GB disk when I booted into my live flash drive.

I modified the menu.lst to allow me to actually see the grub menu, and I selected RECOVERY.   Now the system is reloading, from scratch, and I will rebuild the user.  When the system shipped from RCS, they had an account "rcs" on the system.  I hope I can do away with that on this installation. 

I am learning more about this SWEET little Netbook as I play with it.   Thankfully, I do Ubuntu!!!   LOL


do you?

---

### Post by cfastner on 2009-07-01
I know that there have been some folks in this thread that have complained about the wifi range of the built-in adapter of the Meso.  Has anyone tried a USB wifi dongle?  Particularly, I was thinking about trying a 802.11n adapter.  There is a small one (GW-USMicroN made by Planex) that would really be consistent with the size factor of this computer.  Its inexpensive and if it would increase the range (and speed) it might be well worth purchasing.  But what would it take to get it to work with Ubuntu?

Thoughts anyone?  (Or is everyone else happy with the wifi range?)

Charlie
  ~~~

---

### Post by wabster on 2009-07-02
I know this is going to ruffle a few feathers on this forum because it's primarilly directed at Ubuntu use on the GMeso. However, as I'm one to experiment with most anything, I loaded Windows 7 RC1 to try it out and determine its usability on the GMeso. After using it for about three weeks, I wanted to share with other GMeso owners the results. Basically, it loaded and has run flawlessly! Wifi distance and integrity greatly improved, battery life increased by about 20%, hibernate and sleep functions work perfectly and no noticable slow down in system performance. Of course I greatly miss all the free stuff Ubuntu offers and I consider myself a droid using a Microsoft product. I'll probably revert back to Ubuntu when the RC1 program is over. It's painful to admit MS actually has made a "near perfect" product that works so well on a machine like the GMeso. But I'd need an anti-virus and anti-everything else staying with Windows anything for the long-term. Hail Ubuntu!!

---

### Post by the3dman on 2009-07-20
> **wabster said:**
> I know this is going to ruffle a few feathers on this forum because it's primarilly directed at Ubuntu use on the GMeso. However, as I'm one to experiment with most anything, I loaded Windows 7 RC1 to try it out and determine its usability on the GMeso. After using it for about three weeks, I wanted to share with other GMeso owners the results. Basically, it loaded and has run flawlessly! Wifi distance and integrity greatly improved, battery life increased by about 20%, hibernate and sleep functions work perfectly and no noticable slow down in system performance. Of course I greatly miss all the free stuff Ubuntu offers and I consider myself a droid using a Microsoft product. I'll probably revert back to Ubuntu when the RC1 program is over. It's painful to admit MS actually has made a "near perfect" product that works so well on a machine like the GMeso. But I'd need an anti-virus and anti-everything else staying with Windows anything for the long-term. Hail Ubuntu!!

It is about time they release a halfway decent update from xp. But unfortunately like you said security is and will always be an issue with windows. But I am glad to hear that there is another OS that runs well on the meso. Options are always good.

---

### Post by lincoln32 on 2009-08-03
After 29 pages of reading I wanted to report that I have no concerns on my meso g using 9.04 remix and am totally impressed with this and installed 2g and a 500gig hard drive and other than the tab that will not pop in it been flawless operation for over a month with no concerns that i can find and use it daily as a portable file server.:KS edit 1st concern found' is number lock on and as of yet I have found no instructions to turn it off

---

### Post by Veal_Calf on 2009-08-06
> **lincoln32 said:**
> After 29 pages of reading I wanted to report that I have no concerns on my meso g using 9.04 remix and am totally impressed with this and installed 2g and a 500gig hard drive and other than the tab that will not pop in it been flawless operation for over a month with no concerns that i can find and use it daily as a portable file server.:KS edit 1st concern found' is number lock on and as of yet I have found no instructions to turn it off

I had the same problem with num lock for like 20 minutes, drove me crazy. its right above the -/_ key next to the 0 key. Number lock seems silly to me to have and to have the numbers look like fn buttons too.

---

### Post by Veal_Calf on 2009-08-26
From what I've read everyone has had good experiences with Jaunty. I was thinking about installing it but i seem to have a problem. I can't find the lpia image only the i386 seems to be available on the official download page. So... where can i download the lpia netbook remix image?

---

### Post by wabster on 2009-08-27
Download Ubuntu 9.04 Remix from here:

[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

---

### Post by Veal_Calf on 2009-08-27
> **wabster said:**
> Download Ubuntu 9.04 Remix from here:

[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

I guess maybe I'm missing something... where is the lpia image, because that just lists mirrors to ubuntu-9.04-netbook-remix-i386.img

I've been able to find mirrors for the vanilla ubuntu lpia, or the i386 netbook remix, but not the lpia netbook remix.

---

### Post by wabster on 2009-08-28
Perhaps this is what you're looking for:

[http://cdimage.ubuntu.com/ports/rele...rnate-lpia.iso](http://cdimage.ubuntu.com/ports/rele...rnate-lpia.iso)

---

### Post by wabster on 2009-08-28
Sorry, actually here:

[http://cdimage.ubuntu.com/ports/releases/8.10/release/ubuntu-8.10-alternate-lpia.iso](http://cdimage.ubuntu.com/ports/releases/8.10/release/ubuntu-8.10-alternate-lpia.iso)

---

### Post by wabster on 2009-08-28
Oops, same mistake. Try this:



"http://cdimage.ubuntu.com/ports/releases/8.10/release/ubuntu-8.10-alternate=lpia.iso"

---

### Post by wabster on 2009-08-28
Having a terribly difficult time today:

"http://cdimage.ubuntu.com/ports/releases/8.10/release/ubuntu-8.10-alternate-lpia.iso"

---

### Post by Veal_Calf on 2009-08-29
uh... two things, I think thats 8.10 not 9.04 and its just lpia standard not the netbook remix. 

I was hoping I could install the lpia NBR with little hassle. I guess i could install the lpia vanilla and configure the NBR packages, but I guess it kinda defeats the point of a *Netbook* remix if they don't offer the netbook power optimized image. Is there possibly an easy way to compile an lpia install image or? 

I like the restore image that the Meso comes with, and was hoping that i could get something like that set up to restore a fresh 9.04 NBR. I guess that doesn't sound too clear. I want to install Jaunty and set up a Jaunty recovery partition, like how the Meso comes with Hardy installed and in the recovery.

---

### Post by wuli on 2009-08-30
Hello everyone, 

I just got an onyx Meso which I like very much and I wanted to contribute.  First let me say I have Ubuntu and XP installed on my home PC and I've been using linux on and off in various forms for a few years.  When I stumbled onto the Meso while surfing, I researched it and decided to get one, but I had little luck shopping online.  I did notice though that the Toys R Us website sold it with XP for $200 (though they were also out of stock) so I went to their local store and got the last one for $215.  It had XP, but I loaded UNR 9.04 using a flash stick with materials and instructions from pendrivelinux.com.  

I just applied the fix for the suspend issue from page 28 of this thread (THANKS) and that feature works perfectly now. 

I have had some other interesting issues.  As it's been noted, sometimes after logging in, a blank screen appears.  This only happens for me when I use the classic desktop, so I don't use it.  In the other mode I unclicked Netbook Launcher from the Preferences>Startup Applications menu (for the reason they offer; that it's "clutter-based") so now I have a desktop which isn't the actual desktop, but it's a space I can use to click and drag files, and my cool yellow and black warning stripe wallpaper isn't obscured.  I also have Maximus Window Manager unclicked in the same menu.  I'd seen the blank screen issue mentioned on other forums, but I have yet to find an answer to it.  

Though the Meso I got is still relatively new I haven't run across many problems, and I'm really enjoying it.  :)

---

### Post by keeptrying1188 on 2009-09-03
> **wuli said:**
> Hello everyone, 

I just got an onyx Meso which I like very much and I wanted to contribute.  First let me say I have Ubuntu and XP installed on my home PC and I've been using linux on and off in various forms for a few years.  When I stumbled onto the Meso while surfing, I researched it and decided to get one, but I had little luck shopping online.  I did notice though that the Toys R Us website sold it with XP for $200 (though they were also out of stock) so I went to their local store and got the last one for $215.  It had XP, but I loaded UNR 9.04 using a flash stick with materials and instructions from pendrivelinux.com.  

I just applied the fix for the suspend issue from page 28 of this thread (THANKS) and that feature works perfectly now. 

I have had some other interesting issues.  As it's been noted, sometimes after logging in, a blank screen appears.  This only happens for me when I use the classic desktop, so I don't use it.  In the other mode I unclicked Netbook Launcher from the Preferences>Startup Applications menu (for the reason they offer; that it's "clutter-based") so now I have a desktop which isn't the actual desktop, but it's a space I can use to click and drag files, and my cool yellow and black warning stripe wallpaper isn't obscured.  I also have Maximus Window Manager unclicked in the same menu.  I'd seen the blank screen issue mentioned on other forums, but I have yet to find an answer to it.  

Though the Meso I got is still relatively new I haven't run across many problems, and I'm really enjoying it.  :)
Thanks Wuli for referring us to page 28 for fixing the suspend/wake issue. It worked finally for me. It was such a relief. Everyone having that problem with that function should just follow the instructions n you won't be sorry. Good luck n happy netbooking.

---

### Post by gandhii on 2009-09-21
Running 9.04 nbr i386 here...  recently noticed flash video getting all jumpy when in full screen mode.  Anyone else seeing this issue?

---

### Post by yosef on 2009-09-21
For some reason my headphones are controlled by master in audio and the main speakers do not turn off when I plug in the headphones!  Does anyone know how I can fix this?

---

### Post by stash1 on 2009-11-23
Is the3dman still around? I tried accessing his [www.lowpowertech.com](www.lowpowertech.com) page and i got a "cannot find" message.

I have a problm that several of the keys on the top row are dead (no response) and want to open the case to see if it's (hopefully) a connection, or (fingers crossed) a keyboard-decode chip.
wertop[ are dead, all others appear OK.  I want to take a look at his memory-upgrade pix, if possible, before I open it up.

Any clues? new links? e-mail?

---

### Post by gtrtx on 2009-11-23
I have a copy of the memory upgrade document. I'm at work right now, but I can post it or email it to you if you like. 

I haven't kept up with this thread for a while, but just read over it.
I've since installed 9.10 on my Meso and everything seems to work pretty well out of the box. Suspend and sound are working good. Mostly, the video issues of earlier releases seem to be fixed. I  really recomend 9.10 for this netbook. 

I also had Windows 7 on for a short time. It seemed to function ok as well, but I'm just not that big of a fan of MS. 

> Is the3dman still around? I tried accessing his [www.lowpowertech.com](www.lowpowertech.com) page and i got a "cannot find" message.

I have a problm that several of the keys on the top row are dead (no response) and want to open the case to see if it's (hopefully) a connection, or (fingers crossed) a keyboard-decode chip.
wertop[ are dead, all others appear OK. I want to take a look at his memory-upgrade pix, if possible, before I open it up.

Any clues? new links? e-mail? 

---

### Post by the3dman on 2009-12-05
For everyone wondering what happened to me. Well its a long story, first as far as my website, I had to shut it down. It took me too much time and money to maintain, and I did not have enough subscribers for it to be worth it. So not to long after I shut down my website, my meso decided that it did not want to turn on any more (the motherboard fried), so I tried to get a hold of Sylvania/Digital Gadgets they would not answer their phones or respond to emails. With only 1 month left on my warranty I had to find a way to get a hold of them to fix it. After 2 weeks of phone calls and emails I still got no response. Finally I got sneaky since Digital Gadgets just licenses the name "Sylvania" I figured I would report Sylvania to the BBB in hopes that Sylvania would get mad at Digital Gadgets for making them look bad. It worked!! Within 2 days I had Digital Gadgets on the phone and ready to help. They agreed that it was a bad mother board and said they would ship out a box and shipping label for me to return it to them. After over a week of waiting still no box or label arrived. So yet again I have a hard time calling them but after a few days of trying I got them on the phone for them to tell me that they forgot to send the box and label. So finally I told them to email me a UPS label and I would find a box myself. After shipping it out to them that was the last I heart from them for 2 months!!! Again they would not answer phone calls or emails from me. Finally I got them to answer me by telling them that I was going to report them to the police for theft of my netbook. That got them to respond. They called and said that my meso had a bad motherboard (2 months to figure that out they knew that when they got it) but they didn't have any more meso's to replace it with. So they decided to upgrade me to the Magni Elite. After about 2 more weeks of waiting I had my Magni. I opened it up turned it on and BAM! hard drive faliure. So after another weeks worth of calls and no response I decided to see if I could get western digital to repair the hard drive under warranty. They did and had a new hard drive to me within a week.
So to anyone needing future warranty repairs. Good Luck!!!! Anyway all my files were on the dead meso, so the best I can do for reposing my guides it to re-write them if someone needs help with something specific. -The3dman

---

### Post by Mokele on 2010-01-02
Ha-ha-ha!
Great story!
Well, that's another lesson (buy only known brands)!
I keep following this rule for my fishing equipment and it worked (not a single piece is made in chine). I maybe pay a bit more, but my stuff does not fail after 1 month.
I took a risk with my Meso and I guess I'm just lucky. Still have 8.04 on it and will probably upgrade it to 10.04 when it's out. Works well so far...

---

### Post by PhoebeG on 2010-01-07
Dang, that's a shame, the3rdman.

My meso is going strong, though I just had to order an overpriced adapter for it off of ebay because I lost the original. I've actually been running kubuntu netbook on it. It runs beautifully, and looks beautiful, to boot. Much nicer and more practical design than Netbook Remix, particularly if you get chrome on it. And everything worked perfectly on my first try at an install, too! Would highly recommend it.

Yrs,
Phoebe
[www.phoebeeating.com](www.phoebeeating.com)

---

### Post by wabster on 2010-02-21
Haven't posted in awhile. G meso is still running strong. Was using Windows7 beta on it for the past four months or so which was set to expire. Decided to try Ubuntu UNR 9.10. Loaded easily and the new desktop configuration is a lot cleaner. Performance exceeds 8.10, which was the version I had before moving to the Windows7 test. The wireless modem seems much more stable and connects way faster than the older Ubuntu version. And battery life is as good as it was in Windows7. I had installed an SSD drive in it before loading Windows7, so with 9.10 it is booting and loading WAY quick. Faster than Windows7 (nothing especially new here). I set up a RAM temp and directed Firefox to it, so the internet responds very well. Overall, I think I'm keeping 9.10 back on my G meso. Battery is still hanging in there after one year and this little computer just keeps humming along. I'm still very pleased that I selected the G meso for my netbook.:)

---

### Post by cfastner on 2010-02-22
Wabster:

When you had Windows 7 on the Meso, did you notice any improvement on the range for Wifi?  That is the only thing that I have an issue with my Meso.  The built-in Wifi seems to have a very limited range.  I can't see any neighboring wifi networks (and I KNOW they are there!) and I really can't get too far away from my wireless router!

I actually love MY Meso too!

Charlie
  ~~~

---

### Post by wabster on 2010-02-22
Hello cfastner:

I noticed that wifi range was better with Windows7 compared to UNR 8.10. But since using 9.10 the range is equal to Win7. As I sit here, I'm picking up a UPS store wifi with 3 bars that is about four doors down. I've noticed a considerably stronger performance in wifi with 9.10 and no signal dropping. Much improved over earlier versions. I'm very impressed with 9.10 performance and improvements as you can tell. Runs much faster than Win7 as well.

---

### Post by mttnry on 2010-03-02
a few months ago my meso g died on me.  After a week of inactivity I grabbed it to start it up and it was dead.  I thought maybe the battery was dead so I bought one off ebay and still nada.  I did open it up and checked to make sure every thing was plugged in.  So at this point in trouble shooting im at:
     maybe the cord is fried seeing as the charge light doesnt turn one when it is plugged in.
     power supply fried?
     something else is fried? 
but yeah any help in trouble shooting would be appreciated.  Also if I am not able to fix it ill prolly try to sell it on ebay as is and alert you guys with a link so as you can pick it up for spare parts.

---

### Post by TheKramer on 2010-07-06
Hello everyone.  I got a g meso handed down to me and was attempting to put in new memory.  I did get new memory in with a bit of work, but I'm having trouble getting the keyboard ribbon reattached.

I saw the3dman originally had a guide posted, and that it is now gone.  Does anyone have the guide (or any advice)?  

This is my first real go at my own Ubuntu system (I've worked with other people's before), and it is being ruined by a non-functioning keyboard, hehe.

---

### Post by TheKramer on 2010-07-11
Well, I finally got it back together and working properly.

I still wouldn't mind seeing that guide, though, in case I ever need to go back in there again.

I might be able to give some advice as well if anyone else is thinking about messing around with the RAM.

Basically, the RAM is under the motherboard, and not near the edge.  When you try to pull the motherboard up to get to the RAM (after unscrewing the motherboard from its mounts), you are fairly likely to pull out the monitor cable (not too hard to reattach) and the keyboard ribbon (HARD to reattach).

The to reattaching it was LOTS of light, and good tools: a really long, thin set of needle nose pliers with no "teeth"... probably don't want anything that has too much grip or teeth or you might damage the ribbon and LOTS of light.

I did it by myself, but a second set of hands would be very helpful for lighting and possibly holding the case stable and upright.

Anyway, if that guide doesn't make its way back around, I'll stay subscribed to this thread so that I can try to help if anyone needs it.

---

### Post by TheKramer on 2010-07-15
And... it isn't quite working right yet!  Keyboard is fine, but now the battery won't charge.  Going back in to see if I can figure out what might be wrong.

If anyone has that guide, I wouldn't mind seeing it still in case it can help me trouble shoot this.

---

### Post by DonTarantini on 2010-09-18
This is probably a bit late, but I had to take apart my own Meso G and had an extreme amount of trouble reconnecting the keyboard.
Eventually I got it, it turns out the part where the keyboard connects to there is a black piece and the white bottom hooked up to the motherboard. That black piece is supposed to ROTATE up & down! It clips into the white connection on the board and then you pull it up and it stays, you slip the keyboard wires in and push that black part down, BINGO! Toughest time I've ever had with a computer is that stupid keyboard wire...
Now I'm workin on completely wiping XP from my 8 GB SSD (Since XP takes up 5GB of it after updates!!!) and putting Ubuntu on it.
10.04 Netbook Remix seems alright but I've been hearing about LPIA versions 9.04 & 9.10 working better, even though I'm having some difficulty in getting them to install.
Currently scouring the other 30 pages on this thread, I'm sure I'll figure it out.

---

### Post by wabster on 2010-10-18
Just an update on G Meso experience. Installed Ubuntu 10.10 last week. The netbook version takes up too much screen real estate with the new menu bar. Gotta keep moving the browser screen right and left to see everything. It desperately needs an "auto-hide" option. The new menu bar is a great idea, but poor execution. Rebooted and changed to desktop version. I don't see any perceptible performance change or battery life with 10.04 versus 10.10. May end up just going back to 10.04 netbook version. It seems the new menu bar was supposed to increase screen real estate but I think it did just the opposite.

---

### Post by Channah1973 on 2011-07-24
> **the3dman said:**
> For everyone wondering what happened to me. Well its a long story, first as far as my website, I had to shut it down. It took me too much time and money to maintain, and I did not have enough 
{snip]
.
.
.
So to anyone needing future warranty repairs. Good Luck!!!! Anyway all my files were on the dead meso, so the best I can do for reposing my guides it to re-write them if someone needs help with something specific. -The3dman

> **gtrtx said:**
> I have a copy of the memory upgrade document. I'm at work right now, but I can post it or email it to you if you like. 

I haven't kept up with this thread for a while, but just read over it.
I've since installed 9.10 on my Meso and everything seems to work pretty well out of the box. Suspend and sound are working good. Mostly, the video issues of earlier releases seem to be fixed. I  really recomend 9.10 for this netbook. 

I also had Windows 7 on for a short time. It seemed to function ok as well, but I'm just not that big of a fan of MS.

Both of you don't seem to have been active in a while, but I sure would like to look at that guide.
I opened the case, and the screen, keyboard, and touchpad cables/ribbons all came loose.  It mystifies me how anyone could do anything with them connected, and neither my dad, my brother, or I can get the touchpad ribbon or the keyboard ribbon back in.  My dad was able to reconnect the screen.
The touchpad ribbon seems to want to be just a little bit shifted from the slot were it seems to go, but even when we get it to go in, there seems to be no way to make it lock into place.  If anyone could advise me, it would be greatly appreciated.

---

### Post by MrQuinn on 2013-03-24
I was trying out the webcam, tried cheese but it was laggy and crashed when I tried to record video, then I tried kamoso, which worked really well...until the webcam went black and now just stays black. Removed kamoso, reinstalled, removed it again, installed camorama, cheese again, then kamoso again, still nothing. Should I reformat?

---

