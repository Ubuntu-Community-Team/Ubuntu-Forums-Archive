---
title: "Lightscribe Direct Disk Labeling Software"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by dragonfyre13 on 2005-12-20
OK guys, you've helped me make the switch to ubuntu painless, easy, and efficient. As a bonus, you have also helped everyone I know with ubuntu. All my friends, my business contacts, and even the companies that I do contract work for, are all runnng a version of Ubuntu, and using it at least once a week for something. Now, I'm coming to you with the first problem that I haven't found an answer to on google, this site, or any other places I frequent.

Lightscribe Support is something that is apparently difficult to come by in Linux. I've tried running Wine, Crossover office, and even Cedega for all the different peices of software that do lightscribe. I've tried burning a lightscribe label in qemu, and VMware. None of these work, and they all fail somewhere along the way.

Crossover Office was the closest that I got to burning a label, using windows 2000 mode, and installing the lightscribe host, and Surething CD labeler. after all that is done, sure thing just dies on me on startup. It gives a typical error, (STC terminates with an unexpected fault...)

I'm running an AMD64 machine, with an i386 kernel (I don't want to have to deal with 64 bit anything right now. Opera is the only application that gives me problems with this setup.) I have an HP lightscribe burner.

Ideally, I'd like to find a linux native program that burns lightscribe disks. I've tried NeroLinux, but it doesn't have lightscribe support. I heard on the K3B boards that it should be supporting Lightscribe burning some time in the future, but haven't heard any further.

I'm not above paying for the software, (Up to a point. I suppose about $200 would be my limit) but I need it to work without dual booting.

Right now, this is the only thing I keep my windows partition for. Everything else I can do in either Qemu, crossover office, or cedega. What I can't do, I figure out a way for, or deal without it.

Lightscribe is a big part of my business. I absolutely need this function to carry out my business, and so I dual boot. Spending nearly 7 hours a day in windows, just for this one program (30 minutes per disk) is getting old very quickly.

Are there any programs that do this, even commercial, or can you point me in the right direction?

---

### Post by dragonfyre13 on 2005-12-21
I've never bumped a post before. It gives me chills. ^_^

---

### Post by starfleetcaptainrob on 2006-02-12
I'd like to know the answer to this question as well (if there is one).  I got a Light Scribe DVD burner for Christmas and have to return to XP when I want to use it.

---

### Post by mips on 2006-02-13
As far as I know there is no LightScribe support in linux yet. There is talk that it will appear in K3b though.

---

### Post by dragonfyre13 on 2006-04-06
OK, I got it running under win 2000 under VMware, but that is about it.

---

### Post by mips on 2006-04-10
Apparently Lightscribe is not free and no source has been made available so far...

---

### Post by dragonfyre13 on 2006-04-13
Nope, it isn't free, and I doubt source is going to be released to the public. However, if I could get it running under wine, or K3B would get this going, that would be amazing.

K3B is being sponsored by lacie to put lightscribe support into the K3B burning suite.

---

### Post by mips on 2006-04-14
K3b does not look like it is going to support it for now.

Mail from the developer, Sebastian Trüg:

> lightscribe is not free. hp wanted to provide the sdk, but they didn't...

So there you have it from the horses mouth, maybe one day...

---

### Post by discord on 2006-04-15
thats why i didnt buy a lightscribe burner.

---

### Post by dragonfyre13 on 2006-04-19
[QUOTE=mips]K3b does not look like it is going to support it for now.

Mail from the developer, Sebastian Trüg:



So there you have it from the horses mouth, maybe one day...[/QUOTE]


NOOOOOOO!!!!!

I hadn't heard this. Thanks for the heads up.

---

### Post by hamil on 2006-04-24
I found one post, that stated that maybe Nero for Linux would support Lightscribe.. Can anyone confirm/deny this??

---

### Post by dragonfyre13 on 2006-05-26
Denied. I contacted Nero about it, and they said that they would not be able to support it, or even distibute it because of liscensing issues on linux.

---

### Post by hamil on 2006-05-27
It is a shame... Well, I still have to hang on to Win on one of my machines then... :(
Hope that it some day also will be available for other users than win/mac...

---

### Post by dragonfyre13 on 2006-05-27
No kidding. You would think that at least someone could try and get it working in wine, or something. Since the liscencing terms just say that it has to be only mac and windows native, they could at least work with crossover office....

---

### Post by Sotero on 2006-07-13
Just adding one more name to the list of people who would like to see Lightscribe in linux

---

### Post by Duo Maxwell on 2006-07-18
Add me as well, I'd really like to switch to a light scribe drive given how cheap they've become on Newegg, if only there was linux support...

---

### Post by Coopster on 2006-07-18
I was able to get this working using Windows XP Pro on VMWare player (image created with qemu).  Worked without incident after installing the HP Disk and SureThing labeler.

---

### Post by snowpalmer on 2006-08-29
I'm just going to say that I would love to have lightscribe support for linux.  I have the burner.. would be great to put it to some use! :)

---

### Post by futz on 2006-09-12
One more vote for LightScribe support. I just bought a drive cuz they're cheap and I wanted another burner. I'd like to put it into my main Ubuntu box, but now that I've read this thread I guess it'll go in one of the windoze boxes...

---

### Post by mips on 2006-09-15
Is lighscribe really worth it if you take into consideration how long it actually takes to burn the label onto the cd ???

I suppose it would be nice to do the odd cd now and again but I can't see myself using it on a regular basis at all. The novelty seems to wear off when people have to wait to long for a cd to finish.

---

### Post by Regenerate on 2006-09-17
*putting myself on the I-want-lightscribe-support-for-ubuntu list*

---

### Post by mips on 2006-09-18
Asking here is not goint to help. Go to [http://k3b.plainblack.com/message-board](http://k3b.plainblack.com/message-board)

---

### Post by henrrrik on 2006-10-17
Lacie has released a Lightscribe tool for Linux. I don't have a lightscribe drive myself, but perhaps someone can try it out?

[http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)

---

### Post by matthew on 2006-10-17
My wife's computer has a lightscribe disk in it...I'll try this when I get a chance. It may take a week or so.

---

### Post by mips on 2006-10-18
Seeing it has both CLI & GUI interfaces it would probably be possible to integrate/link into K3b.

---

### Post by Headrush on 2006-10-19
[http://www.kde-apps.org/content/show.php?content=47458&PHPSESSID=4a0d61d2d0db3decca0f70095720889f](http://www.kde-apps.org/content/show.php?content=47458&PHPSESSID=4a0d61d2d0db3decca0f70095720889f)

---

### Post by metalqga on 2006-10-27
I'm interested in software capable of burning labels via the Nec's LabelFlash technology. I have a NEC 4551 but haven't used this function since I converted to Ubuntu. 
It's not something to die for, but it's better to have everything functioning.

---

### Post by pld on 2006-10-30
Just wanted to confirm that LaCie's 4L software is working as advertised in Dapper, using an LG external usb writer.

---

### Post by StefAndrew on 2006-10-31
Can anyone else confirm they're having trouble with 4L software and Edgy?  It doesn't want to detect my drive.  The program starts up fine, but I can't actually burn the image because it doesn't see my drive.

---

### Post by matthew on 2006-10-31
> **matthew said:**
> My wife's computer has a lightscribe disk in it...I'll try this when I get a chance. It may take a week or so.Small update...I got this running on my wife's computer which uses Dapper...but I haven't been able to find any LightScribe disks in Morocco to test it. The software seems to work fine, but the lack of media makes it impossible to be certain. Sorry.

---

### Post by Megatog615 on 2006-10-31
I get a segfault when trying to do "4L-cli enumerate". Anyone else have this problem?

---

### Post by mcsix on 2006-11-01
I have the same problem. It worked fine in Dapper but does not work in edgy for me. It does not detect my drive in gui and I get the segment fault in cli enumerate also.

---

### Post by anttix on 2006-11-02
Don't know about ubuntu, but in Fedora Core 6 I needed to do this to get the LaCie binary only piece of .... to recognize my writer:

cd /dev
ln -s scd0 sr0

---

### Post by laberer on 2006-11-02
I also get the Segmentation fault in Edgy...a symbolic link to my dvdrecorder didn't solve the problem.

---

### Post by Megatog615 on 2006-11-02
> **anttix said:**
> Don't know about ubuntu, but in Fedora Core 6 I needed to do this to get the LaCie binary only piece of .... to recognize my writer:

cd /dev
ln -s scd0 sr0

That did not solve the problem. It would seem a lot of people have this problem, too...

---

### Post by seanUSXIII on 2006-11-13
I'm getting the same segfault :(

Anyone?

---

### Post by KeithUK on 2006-11-14
Yes, I get a segfault also. Probably a source recompile needed due to changed headers or something.

I've registered with LaCie as a user of the software and raised a bug report. I'll let you know what transpires.

---

### Post by bg1256 on 2006-11-16
This thread was brought to my attention by another forum member, so I thought I'd bump it to see if any of you have had success running this in Edgy yet.

If so, how?

---

### Post by bg1256 on 2006-11-16
Well, I got it installed and running on Edgy, but when I finally got the picture selected and attempted to print it, the program said that it was forced to quit unexpectedly.

So, sounds like I'm still having the same problem as everyone else?

---

### Post by StefAndrew on 2006-11-16
I can get it installed and working properly up until I try to burn the image.  It doesn't recognize my burner as being a lightscribe burner and won't let me burn.

---

### Post by seanUSXIII on 2006-11-16
> **StefAndrew said:**
> I can get it installed and working properly up until I try to burn the image.  It doesn't recognize my burner as being a lightscribe burner and won't let me burn.

This is because the daughter-program 4l-cli segfaults. Since its closed source, we just need to wait and see if the afformentioned bug report gets LaCie to recompile the binaries

---

### Post by fluffd on 2006-11-18
ioctl{3, SNDCTL_TMR_TIMEBASE or TCGETS, 0xbfaf99b8} = -1 ENOTTY (Inappropriate ioctl for device)

This is the area I get when i run 4L-cli through strace.
That and some of them are errors about reading the device status. I'll see if  I can find a way to fix this if lacie doesnt update quick enough.

---

### Post by PilotJLR on 2006-11-24
Same problem here with Edgy...

I've opened a ticket with LaCie for this. Maybe if everyone who has this issue and owns LaCie hardware will open a support ticket, then they will be motivated to update the program to work under Edgy.

---

### Post by timcredible on 2006-11-24
.  oops, duplicate info, please ignore

---

### Post by johanjpk on 2006-11-25
Hi, 

I couldn't get it to work either... but dit anyone look into this? 
[URL="http://www.lightscribe.com/downloadSection/linux/index.aspx"]
http://www.lightscribe.com/downloadSection/linux/index.aspx[/URL]

Maybe for people that are more smart than me can make it work. 

greetings 

Johan

---

### Post by PilotJLR on 2006-11-26
> **johanjpk said:**
> Hi, 

I couldn't get it to work either... but dit anyone look into this? 
[URL="http://www.lightscribe.com/downloadSection/linux/index.aspx"]
http://www.lightscribe.com/downloadSection/linux/index.aspx[/URL]

Maybe for people that are more smart than me can make it work. 

greetings 

Johan

No, afraid not... it appears to be the same base software as with the LaCie rpm's.

Using the packages on this link, I get the same segfault.

---

### Post by StefAndrew on 2006-11-27
"Debian-based distrobutions such as Ubuntu are currently not supported."

Guess we're still waiting, huh?

---

### Post by hamil on 2006-11-27
Well, I did send the Lightscribe team a positive feedback. Positive, since what they have done proves that they also approves their customers which is currently not using MS. In the same mail, I also let them knew that I was not able to use the RPM packages. Today, I recieved a answer. Just to let you all know, here is the answer from Lightscribe:

> 
Hello Lasse,
 
Thank you for your feedback. 
 
We do know that even converting the .rpm installation file to .deb format using alien, there are still some conflicts that prevents the LightScribe System Software from installing and operating properly on debian-based distributions.  We are investigating this and apologize for this inconvenience. 
 
If you have further questions,  please reply to this message.
 
Best Regards,
xxx xxxx


So, it do mean that they are working on some kind of solution. If we have waited this long, we can surly wait a little longer.. ;)

---

### Post by PilotJLR on 2006-11-27
I got a response from LaCie tech support... good news!

> Hello,

Ubuntu 6.10 was released 10-26-2006. While our Labeler was tested with 6.6 it was not tested with 6.10. We are in the process of doing so. Keep an eye on our website for future updates. 

---

### Post by StefAndrew on 2006-11-28
Very good news.  Hopefully soon we can all have Lightscribe working properly.

---

### Post by KeithUK on 2006-11-29
I raised a support ticket with LaCie (Ticket #: 100002882) and have been having a lengthy conversation with one of their technical guys.

His problem was that LaCie internal people are sticking with Dapper because of the long term support aspects. However, not to be outdone he downloaded a copy of the Edgy install and installed it on a system of his own. He gets the same results, i.e. a segfault.

He was hopeful that it was as simple as a missing library somewhere but we have now come to the conclusion that a rebuild is required under the later kernel sources of Edgy.

I've had to recompile a couple a drivers because of kernel source changes that occurred corresponding to the Edgy release, so it doesn't surprise me.

I'm waiting for him to get back to me but, obviously, it's not a high priority and they have to fit it in with more immediate support efforts.

I'll keep you all posted.

---

### Post by Bobonov on 2006-12-01
The lightscribe sdk has been released for linux system, there are also some software in rpm.

[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

---

### Post by iceberg on 2006-12-01
Yes, but to be useful, you must install the lightscribe software and this one is currently not available for edgy. We're all waiting for a fix ;)

---

### Post by bg1256 on 2006-12-02
> **Bobonov said:**
> The lightscribe sdk has been released for linux system, there are also some software in rpm.

[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

[QUOTE=posted link]
Debian-based distributions such as Ubuntu are currently not supported.[/QUOTE]
Says it all, for the moment.

---

### Post by pengu on 2006-12-02
has anyone tried installing the rmp on ubuntu with alien???

thanks

---

### Post by tlacuache on 2006-12-02
> **pengu said:**
> has anyone tried installing the rmp on ubuntu with alien???

thanks

Yes. Have you read the thread? The rpm's install ok, and I guess they run in Dapper, but in Edgy they cause a seg fault. So basically we're all waiting for them to recompile the binaries for the latest Ubuntu release.

---

### Post by spazsui on 2006-12-02
I tried and had no success.  Being a newb still, I guess I need someone smarter than me to convert it to deb packages and then post them somewhere so I can get it done!

---

### Post by bg1256 on 2006-12-03
I'm running Automatix2 on Edgy, and after I updated my system today, I noticed that LaCie's lightscribe software made it into Automatix.  I installed it and am about to try it now.

---

### Post by bg1256 on 2006-12-03
Well, that didn't work ](*,)

---

### Post by arnieboy on 2006-12-03
> **bg1256 said:**
> Well, that didn't work ](*,)
Automatix installs Lightscribe in Applications ->Accessories on Ubuntu Edgy

---

### Post by bg1256 on 2006-12-03
He, gotcha. I thought maybe since it had made it to Automatix, that it had been fixed for us.

Thanks for pointing that out to me.

---

### Post by PilotJLR on 2006-12-17
I have some more information on the Lightscribe / Edgy debacle...

I attempted to make a VMware virtual machine that will allow me to effectively burn a Lightscribe label in Edgy, but it was only marginally successful.
I basically made a Dapper VM, gave it virtual SCSI access to the burner, and tunneled X over SSH in order to make the application appear local to the host Edgy desktop. The burn works in this manner, but the edges of the Lightscribe label are very faint.
The inner third of the disc label burns well, but the edges are extremely faint, so I don't consider this solution to be viable.
I'm guessing the problem may be that the VM can't send I/O requests quickly enough through the VM abstraction layer to the device, but that's just an educated guess.

So I'm pretty much still waiting and hoping LaCie or someone makes an Edgy-compatible version!

---

### Post by po0f on 2006-12-18
Funny thing happened, I just bought my LightScribe drive (one of the new 18x jobbies) about 2 weeks ago and finally got tired of waiting.  Tried to put Dapper on it, and guess what?  The drive is too new for the Dapper's kernel to recognize, I/O errors out the wazoo.  :)  (I *could* scrounge up an older optical drive from the spares I have lying around, but I don't feel motivated enough to pull my box out and tinker with it's privates at the moment.)

I was thinking maybe a chroot'ed Dapper environment would be better than a VM environment.  Haven't tried anything beyond thinking about it though.

I might get rid of my FreeBSD install and put FC6 on the spare drive...

---

### Post by bg1256 on 2007-01-08
Just a little bump.

Just curious if there is any news from those who have registered with Lacie.

---

### Post by Biitsch on 2007-01-12
That's what I got:

Original text from lacie.de (Nov 29, 2006):
>Momentan gibt es einige Probleme mit Ubuntu 6.10. Die Produkt Manager sind dabei, die
>Ursache des Problems zu identifizieren und eine Lösung zu finden. Leider steht momentan
>noch kein Zeitpunkt für ein entsprechendes Update fest. 

I tried to translation that into:
Currently there are a few problems with Ubuntu 6.10. The product managers are busy trying
to identify the source of the problem and to find a sollution. Unfortunately there ist currently
no scheduled time for the release of an appropriate update.

Doesn't sound like beeing a top issue for them.

---

### Post by Arukuro on 2007-01-18
I am aware that it has been some time since the last poster but there is a lightscribe program for linux it is available through the laci website or through automatix that is where i found it and im using kubuntu if anyone needs to know and all i did was use the automatic installer in kubuntu and i got it to work just fine so happy hunting and good luck hope this helps out anyone with the need

---

### Post by PilotJLR on 2007-01-18
> **Arukuro said:**
> I am aware that it has been some time since the last poster but there is a lightscribe program for linux it is available through the laci website or through automatix that is where i found it and im using kubuntu if anyone needs to know and all i did was use the automatic installer in kubuntu and i got it to work just fine so happy hunting and good luck hope this helps out anyone with the need

Yes, this program works on Dapper - NOT of Edgy... that is the whole point of this thread...

---

### Post by djrenown on 2007-02-05
bump... is there any thing new on the lightscribe front.  I as well as everyone here am gettin a seg fault and my lightscribe external burner is not being recognized.

---

### Post by HyperY2K on 2007-02-11
what is exactly the problem?  I use this [Debian-Packet]("http://www.kekz-box.de/download/4l_1.0-r6_i386.deb") and the GUI seemed to work. Currently, I never try to "burn" an image on the back of a DVD, but it seem to work? DId anybody try version 1.0r6 of the Lacie -Software?

---

### Post by PilotJLR on 2007-02-11
The GUI is fine. If you try to actually burn a label, you get a segmentation fault.

---

### Post by laberer on 2007-02-16
I also always got the segmentation fault error.

But with the new lightscribe-**1.4.142.1-**linux-2.6-intel.rpm host software from lightscribe.com it finally works!

---

### Post by bg1256 on 2007-02-16
What works?  The GUI or actually burning a label?

---

### Post by laberer on 2007-02-17
I mean burning a label works now, as it did in dapper.

The gui was always "working", but before the 1.4.142.1 driver software, my dvd burner (LG GSA H22L) wasn't recognized in the gui. In the terminal and with 4L-cli enumerate i could see the "segmentation error"...but as i said now it's all fine.

[I'm using feisty with the 2.6.20-8 kernel]

---

### Post by jgarff on 2007-02-20
I just tried 1.4.142.1 and I still get a segfault when running 4L-cli enumerate on edgy with custom 2.6.20 kernel.  Any other suggestions?

---

### Post by taavi on 2007-02-27
> **mips said:**
> Is lighscribe really worth it if you take into consideration how long it actually takes to burn the label onto the cd ???

I suppose it would be nice to do the odd cd now and again but I can't see myself using it on a regular basis at all. The novelty seems to wear off when people have to wait to long for a cd to finish.
I really would like to have some my favourite netlabel releases designed fancy, so they would look cool to play them somewhere (DJing). Many netlabels offer full graphics for designing your own releases!

---

### Post by Shadoglare on 2007-03-06
Well, crap - and I just installed my new Asus lightscribe drive too :(

I've tried the newest version of the back-end from the lightscribe.com site and get the segfault *sigh*.

---

### Post by watson540 on 2007-03-06
And there IS a fix for this if you're running on edgy. Works out of the box on Dapper, so you have to make a dapper chroot and run the app from there. Poof has made an awesome howto on these forums. Just do a search for lightscribe and you will see it. Good luck :)

P.S. - I'm burning a label right now, running an X server under chrooted dapper :), a bit overkill, it is. But we gotsta do what we gotsta do

---

### Post by ripplegold on 2007-03-14
These guys CLAIM to support linux, but only the sellout Radhatters and SuSers, no lightscribe for sLaX or Humans i supose. Anyone know how to port the RPMs to Ubuntu Packets and/or Tarz? Too bad no source code....

---

### Post by ripplegold on 2007-03-14
Forgot the linx

[http://www.lightscribe.com/downloadSection/linux](http://www.lightscribe.com/downloadSection/linux)

[http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814)

---

### Post by PilotJLR on 2007-03-15
> **ripplegold said:**
> These guys CLAIM to support linux, but only the sellout Radhatters and SuSers, no lightscribe for sLaX or Humans i supose. Anyone know how to port the RPMs to Ubuntu Packets and/or Tarz? Too bad no source code....

Lots of people use rpm and redhat; it's not a 'sellout'.

To convert to debian, use the alien tool:
```

sudo apt-get install alien
alien <name of rpm file>

```

---

### Post by bennyj on 2007-03-25
I converted both the host system software and the application software off the lightscribe website to deb packages using alien.installed them.Went into Places>computer>filesystem>usr>4L and clicked on the 4L-gui(installing using the deb did not add it the the application menu) and it worked fine under fiesty 7.4.

---

### Post by KeighleHawk on 2007-04-05
I did this and did not seem to get the 4L-cli or 4L-gui programs.  I did get one called SimpleLabeler in /var/opt/lightscribeapplicaitons/SimpleLabeler that does not run yet.  It complains about libpng so I'll go look into that.

However, could you be more explicit about what you did?

---

### Post by KeighleHawk on 2007-04-05
I seem to have located the 4L-cli and 4L-gui packages (found in an earlier post) and have them installed now.  I now have the same problem mentioned by laberer.  It does not show the device in the drop down box.  I also get the core dump with 4L-cli enumerate.

laberer, how did you fix this?  Is moving to fiesty the fix?

---

### Post by bennyj on 2007-04-05
> **KeighleHawk said:**
> laberer, how did you fix this?  Is moving to fiesty the fix?

You do have a lightscribe enabled drive right ? You have not mentioned that you do.the software will only dectect Lightscribe enabled drives.

other than that I did a clean install of fiesty, installed the software as stated above and it detected my drive and worked fine.

---

### Post by wactuary on 2007-04-12
> KeighleHawk Said:  	I did this and did not seem to get the 4L-cli or 4L-gui programs. I did get one called SimpleLabeler in /var/opt/lightscribeapplicaitons/SimpleLabeler that does not run yet. It complains about libpng so I'll go look into that.

For me, it was in /opt/lightscribeApplications/.  I found that there is libpng12 package installed by default from the main repositories, but there is also a beta libpng3 in either Universe or Multiverse.  Install that, then the program runs fine.

```
sudo apt-get install libpng3
``` 

This is a REALLY basic labeler, just enough to prove the lightscribe drive is detected and functions.

I then downloaded and installed using the alien method referenced earlier, the Lacie 4L program.  I also downloaded some of the sample designs from the lighscribe.com site.  Lacie 4L required root priveleges, so to get it to burn the label, I did this:

Navigate to /usr/4L/ and right-click on the 4L-gui icon.  Select Open with Other Application... and then choose Custom Command.  Use the command "gksu %1".  Alternately, just type ```
gksu /usr/4L/4L-gui
``` from a terminal window.  I'll have to look into out why this program requires root, but the other SimpleLabler program could draw without root permission.

I hope this is helpful to some.  I can report full success in Feisty (Beta), using an Asus DRW-1814BLT sata drive. 

Chris

---

### Post by hoggbottom59 on 2007-04-14
There is support for RPMs but not for Ubuntu yet.

[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

Leon.

---

### Post by PilotJLR on 2007-04-14
> **hoggbottom59 said:**
> There is support for RPMs but not for Ubuntu yet.

[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

Leon.

So I guess everyone here is just making this up then, huh? At least **skim** the thread before you post.  :eek:

---

### Post by go_dragons on 2007-04-20
There IS now lightscribe support for linux. There is not currently any support for debian-based distros but an rpm for the required software can be found here: [http://www.lightscribe.com/downloadSection/linux/]("http://www.lightscribe.com/downloadSection/linux/")

I have not heard of anyone trying to install this yet in ubuntu, but I presume it could be done somehow. I'll be checking back to see if anyone gets this working! I'd be interested to know.

---

### Post by 0be1 on 2007-04-20
Not sure of all the lib requirements etc. but I just utilized the above information, but I will tell you exactly what I did and it worked perfect.

1) $sudo apt-get update
$sudo apt-get install alien

Once Alien is installed then I went to:

[http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)

downloaded to my desktop (choose your own location if you wish)

[http://www.lacie.com/support/drivers/driver.htm?id=10095](http://www.lacie.com/support/drivers/driver.htm?id=10095)
[http://www.lacie.com/support/drivers/driver.htm?id=10094](http://www.lacie.com/support/drivers/driver.htm?id=10094)

Go to a terminal session and sudo su

switch to the directory you downloaded the above files to and type:

alien -k --scripts *filename*       - i.e) alien -k --scripts lightscribe_1.4.136.1-0_i386.rpm

afterwards it should saw .deb file created. Double click on the .deb file to install

repeat procedure for the second file.

Once the files are installed in your terminal session type cd/usr/4L and hit enter

type 4L-gui and hit enter

You should now have the lightscribe program up and running.

I just made a CD label and it worked FANTASTIC!!!!

Happy Burning :o)

0be1

---

### Post by PilotJLR on 2007-04-20
Yes, it works in ubuntu. Alien allows you to install rpm files in a debian based system.

Those running Edgy will need to make a dapper chroot environment as explained by someone else in this thread.

---

### Post by johng4 on 2007-04-21
There is a lightscribe linux port.  Its just not available for debian-based linux yet.

PCLinuxOS has it in their repos, the isntallation is painless, and the software works without a hitch.  I split a good amount of my time between PCLOS and Ubuntu for reasons like this.  Though I love Feisty Fawn, there's just a small set of programs that I can't live without that PCLOS has.

---

### Post by johng4 on 2007-04-21
you might try going to the lightscrive site, and use "alien" on the lightscribe rpms.  I havent tried it since I've got a PCLOS installation already installed with it working.

---

### Post by reiki on 2007-04-24
I installed this on **Feisty** (the release... fully updated)  just last night to try it.

I downloaded Lightscribe_1.4.142.1.rpm from lightscribe.com and also downloaded LS Simple Labeler 1.4.128.1.

I used alien to turn them into debs. You may need to use sudo alien --scripts on one of those files but I don't remember which one. I think it was the system software (Lightscribe_1.4.142.1.rpm). I did it WITHOUT the --scripts parameter and got a warning at the end that I may need to run it WITH that parameter. So I ran it again on that one file.... it worked both times as far as converting it, but I actually INSTALLED the one I used the --scripts parameter on... hope that makes sense..

You need to install the system software FIRST before the labeler.

After converting and installing 4L-1.0-r6.i586.rpm I ran the following:

sudo /usr/4L/4L-cli enumerate
--this is a command line app that enumerates the drives available. Not sure if I NEEDED to run it, but I did. It found my Samsung SATA SH-S183L DVD burner.

sudo /usr/4L/4L-gui
--this opens the actual labeling software. Simple, but pretty neat.

So this does work on Feisty just by using alien to convert the RPMs to DEBs

Enjoy!

---

### Post by Shay Stephens on 2007-04-24
I have lightscribe working too in Feisty.  I turned the two RPM's into deb's and installed them.  I run it like this:
```
gksudo 4L-gui
```

I could never get it to work in Edgy, only Dapper, and now Feisty!

---

### Post by volksolwagen57 on 2007-04-24
i downloaded a similar program and converted it and all that good stuff. it works to a certain point. 
i do this:
4L-gui
and that's it the gui then let's me retrieve  a lable image. so i flipped my dvd over, wait for it to mount as cd-r and tried to burn it **but** lacie does not recognize any drives. what the heck? 
can someone help me out with this? i've almost got it working. thanks in advance.
oh, shoot! i accidentally installed the second piece of software only.

---

### Post by volksolwagen57 on 2007-04-24
i successfully installed both pieces of software, now it detects my hp dvd burner but also i cannot burn the image because i get this error:
Printing requires root privileges.
How can I fix this?

---

### Post by drpaul on 2007-04-24
To Volkswagen57

See reply #94

Paul

---

### Post by reiki on 2007-04-24
Ok I burned my first label using 4L. I have to say it's kind of a sparse program. I imported an image and when I tried to import a SECOND image, it just replaced the first one with the second. So like... I couldn't bring in 2 images and place them in different locations on the disk. And with ONE image... I couldn't type any text on the disk. I think I have to work with it a bit.

---

### Post by Shay Stephens on 2007-04-25
> **reiki said:**
> Ok I burned my first label using 4L. I have to say it's kind of a sparse program. I imported an image and when I tried to import a SECOND image, it just replaced the first one with the second. So like... I couldn't bring in 2 images and place them in different locations on the disk. And with ONE image... I couldn't type any text on the disk. I think I have to work with it a bit.

I create my finished image, import that and burn it.  Works great and you have maximum control.

This is the template I use:
[http://www.shaystephens.com/graphics/lightscribe_template.gif](http://www.shaystephens.com/graphics/lightscribe_template.gif)

The red area of the template is the writable area, you can use it to layout your own template designs.  And it doesn't need to be resized when imported to 4L-gui, just import and print.

---

### Post by reiki on 2007-04-25
Thanks, Shay! I'll give that a try. I have a question for you, though. In one of  my posts above I mentioned using alien on Lightscribe_1.4.142.1.rpm. In actuality, it was Lightscribe_1.4.136.1.rpm because my copy of Lightscribe_1.4.142.1.rpm is "not an rpm" according to alien. I'm pretty sure this has something to do with the fact that when I try to download an rpm, my browser tries to PLAY it in media player! :)

Did you manage to get a good copy of 1.4.142.1?

OH!  And did you run alien using the --scripts parameter or without it? I haven't yet learned how to look inside teh rpm and see what those scripts ARE, but.... I think some of it had to do with assigning group permissions.

---

### Post by Shay Stephens on 2007-04-25
> **reiki said:**
> Thanks, Shay! I'll give that a try. I have a question for you, though. In one of  my posts above I mentioned using alien on Lightscribe_1.4.142.1.rpm. In actuality, it was Lightscribe_1.4.136.1.rpm because my copy of Lightscribe_1.4.142.1.rpm is "not an rpm" according to alien. I'm pretty sure this has something to do with the fact that when I try to download an rpm, my browser tries to PLAY it in media player! :)

Did you manage to get a good copy of 1.4.142.1?

OH!  And did you run alien using the --scripts parameter or without it? I haven't yet learned how to look inside teh rpm and see what those scripts ARE, but.... I think some of it had to do with assigning group permissions.

I downloaded 
[lightscribe-1.4.136.1-linux-2.6-intel.rpm]("http://www.lacie.com/support/drivers/driver.htm?id=10095")
[4L-1.0-r6.i586.rpm]("http://www.lacie.com/support/drivers/driver.htm?id=10094")
From the lacie website, then I ran from within the download folder
```
sudo alien lightscribe-1.4.136.1-linux-2.6-intel.rpm
sudo alien 4L-1.0-r6.i586.rpm
```

I then double clicked on the following generated deb files
lightscribe_1.4.136.1-1_i386.deb
4l_1.0-1_i386.deb
and intalled them with gdebi.  To run it, I created a launcher and used the following command
```
gksudo 4L-gui
```

---

### Post by reiki on 2007-04-25
Ok thanks. I think the --scripts parameter allows it to change permissions ... something about a group called "wheel" which I THINK in rpm-based distros is a group that's runnable by non-root users. As long as the gksudo 4L-gui works, I'm content to use it that way. :)

---

### Post by Shay Stephens on 2007-04-25
This is the info I have on making your own template from scratch:

**Lightscribe Specs:**
Printable area begins 2.38cm and goes to 5.87cm radius
Resolution at least 600dpi max 1200dpi

**CD Spec's**
120mm in diameter with a central 15mm diameter hole.  
The active area begins at 46mm and ends at the 117mm diameter

---

### Post by HyperY2K on 2007-04-30
so lightscribe works for you i 7.04?

---

### Post by reiki on 2007-04-30
yes, I have it in Feisty (7.04). I have admittedly not even TRIED it in Edgy as I am now booting to Feisty as a daily operating system and I keep Edgy on there for emergencies :)

---

### Post by Shay Stephens on 2007-04-30
> **reiki said:**
> yes, I have it in Feisty (7.04). I have admittedly not even TRIED it in Edgy as I am now booting to Feisty as a daily operating system and I keep Edgy on there for emergencies :)

Lightscribe works in Feisty but not Edgy.  It will work in Dapper however.

---

### Post by tekno62 on 2007-04-30
I get " print requires root privileges " any help please

---

### Post by Shay Stephens on 2007-05-01
> **tekno62 said:**
> I get " print requires root privileges " any help please

Like I mentioned, you have to run 4L-gui via gksudo, like this:
```
gksudo 4L-gui
```

---

### Post by go_dragons on 2007-05-18
Has anyone tried to do this with AMD64? When I try to use alien it gives me an error

dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)

I couldnt find an rpm for the amd64 architecture. I am sure there is a simple way to get around this but I am a noob and I dont know what it is. Thanks for your help.

---

### Post by Dazed_75 on 2007-05-21
I had no trouble installing in Feisty, but I am very puzzled about the utility of 4L.  It appears to me that ALL image and text preparation must be done outside of 4L.  There seems to be no utility whatever for the 3 bottom left buttons UNLESS 4L simply uses them to restrict what part of the image yoou provide is considered for printing.  

What am I not understanding?

And if I am right, what do people use to edit the template images?  Using GIMP seems like huge overkill and a difficult way to create textual disc labels.

So far it seems easier to boot up a Windows box with a lightscribe drive and decent labeling s/w to do this job.

---

### Post by Shay Stephens on 2007-05-21
> **Dazed_75 said:**
> I had no trouble installing in Feisty, but I am very puzzled about the utility of 4L.  It appears to me that ALL image and text preparation must be done outside of 4L.  There seems to be no utility whatever for the 3 bottom left buttons UNLESS 4L simply uses them to restrict what part of the image yoou provide is considered for printing.  

What am I not understanding?

And if I am right, what do people use to edit the template images?  Using GIMP seems like huge overkill and a difficult way to create textual disc labels.

So far it seems easier to boot up a Windows box with a lightscribe drive and decent labeling s/w to do this job.

You have it right.  You have to create the label outside of the 4L program.  I create mine in Photoshop 7, save a jpg, load it into 4L and print the disks.  This is how I have always done it though as I tend to use custom templates that are more complicated than the typical disk printing software can deal with.

So for me having 4L simply do the printing is nice and efficient.  The trick to having a quick layout is to make a template that you just edit the text on.  That way you don't have to do any fiddling or design work, just type and save as jpg.

---

### Post by becatlibra on 2007-05-26
[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

There is a labeling app there - for LINUX.  Haven't tried it yet but it appears to be a free download.

-B

---

### Post by reiki on 2007-06-06
For FEISTY users (I have not tried this in Edgy or Dapper or anything else)

I have the Lightscribe System Software as a .deb [here]("http://www.yardbird.net/lightscribe/lightscribe_1.6.45.1-0_i386.deb") 
This is lightscribe_1.6.45.1.rpm turned into a .deb using alien -k-c.
You need to install that one first.

Then I have the Lightscribe Labeler [here]("http://www.yardbird.net/lightscribe/4l_1.0-r6_i386.deb")
Install that one second.

You still have to run 4L as sudo so to start it:

sudo 4L-gui

Otherwise you won't be able to print (burn the lightscribe image to the media)

I'll leave those up as long as I don't have bandwidth problems from doing so :)

---

### Post by Megatog615 on 2007-06-07
So I can get rid of my Dapper chroot now?

---

### Post by reiki on 2007-06-10
> **Megatog615 said:**
> So I can get rid of my Dapper chroot now?

I don't make any guarantees with this stuff. :)  
I can only tell you that I have installed this on at least 4 different Feisty installs from the files I linked to in the previous post and all have worked with no issues.

---

### Post by diesel1 on 2007-06-14
> **reiki said:**
> For FEISTY users (I have not tried this in Edgy or Dapper or anything else)

I have the Lightscribe System Software as a .deb [here]("http://www.yardbird.net/lightscribe/lightscribe_1.6.45.1-0_i386.deb") 
This is lightscribe_1.6.45.1.rpm turned into a .deb using alien -k-c.
You need to install that one first.

Then I have the Lightscribe Labeler [here]("http://www.yardbird.net/lightscribe/4l_1.0-r6_i386.deb")
Install that one second.

You still have to run 4L as sudo so to start it:

sudo 4L-gui

Otherwise you won't be able to print (burn the lightscribe image to the media)

I'll leave those up as long as I don't have bandwidth problems from doing so :)




Ok, if I could get this to run on Dapper64 instead of Feistyi386 I would be happy!


Diesel1.

---

### Post by loyeyoung on 2007-06-20
**[SIZE="4"]SECURITY ISSUE[/SIZE]**: It's a BAD idea to do anything but system administration in the root account.

**[SIZE="4"]BEFORE INSTALLING THE LIGHTSCRIBE SOFTWARE[/SIZE]**, create a user group called "wheel", and add to it the users that you want to use the LightScribe software. THEN install the apps. After that, you won't need to run the applications as root. 

Here's how (substitute yourusername with your actual username):

# sudo -s
[enter your password when prompted]
# addgroup wheel
# adduser yourusername wheel
[repeat as necessary for all users you want to use the Lightscribe drive]

The re-install the packages.


Also, there's a typo in the path to one of the packages, so installation may hang unexpectedly. If it doesn't hang, it will at least give you problems, now or in the future. Here's how to fix:

Open a terminal or console and become root.
# sudo -s
[enter password when prompted]
# mv /usr/share/doc/lightscribeLicense.rtf.gz /usr/share/doc/lightscribe/License.rtf.gz 
# cd /usr/share/doc/lightscribe
# gunzip License.rtf.gz
# ln -s License.rtf /usr/share/doc/lightscribeLicense.rtf

Then reinstall. After the reinstall, run the following (still as root):

# cd /usr/share/doc/
# rm lightscribeLicense.rtf
# mandb
# exit

Happy Trails,

Loye Young
[http://www.iycc.biz](http://www.iycc.biz)
Laredo, Texas

---

### Post by bennyj on 2007-06-20
Has anyone checked out this [http://www.lightscribe.com/downloadsection/pse/index.aspx?campaign=1573&recipient=779800&link=download2]("http://www.lightscribe.com/downloadsection/pse/index.aspx?campaign=1573&recipient=779800&link=download2")

It has 2 packages for linux.you will need to install the Lss package first then install the simpleLabeler package.After installation you can find the luancher in /opt/lightscribeApplications/.From there you can just add it  to your menu.

Hope this helps

---

### Post by Sciamano on 2007-06-24
> **Megatog615 said:**
> So I can get rid of my Dapper chroot now?

I'm in the same situation... now 4L works withouth the chroot, but I have no idea about how to "uninstall" all that chroot thingy we had to do to make it work in Edgy.
Any help about this?
Does deleting the dapper_chroot dir do the trick? Or does it need something else?
Thanks

---

### Post by PilotJLR on 2007-06-28
Be very careful with removing the chroot environment. Remember that it has symlinks to home, dev, and other important stuff. So don't just delete the whole directory, unless you explicitly remove the symlinks!!

---

### Post by Sciamano on 2007-06-28
> **PilotJLR said:**
> Be very careful with removing the chroot environment. Remember that it has symlinks to home, dev, and other important stuff. So don't just delete the whole directory, unless you explicitly remove the symlinks!!

I thought the symlinks point from the chroot environment to Edgy's (now Feisty's) files and directories.. if this is the case, why should removing the chroot environment cause any problem?
I don't get it (probably I got it all wrong...)

---

### Post by PilotJLR on 2007-06-28
You're right - they do point to the edgy/feisty files. What I mean is that if you were to a (don't do this) "sudo rm -rf /dapper_chroot" then that would also remove stuff inside those symlinks. 
So deleting the parent would also cause the linked items to go away too.

I found this out the hard way. I was kicking myself for not thinking of it during the couple hours it took to rebuild.

---

### Post by Sciamano on 2007-06-28
Thanks PilotJLR for pointing this out!
I didn't know that!
How can I safely remove the dapper_chroot dir, then?

---

### Post by maxim_86ualb2 on 2007-07-02
Thank you for your post, helped me a lot :) one typo... 
> **loyeyoung said:**
> **[SIZE="4"]SECURITY ISSUE[/SIZE]**: It's a BAD idea to do anything but system administration in the root account.

**[SIZE="4"]BEFORE INSTALLING THE LIGHTSCRIBE SOFTWARE[/SIZE]**, create a user group called "wheel", and add to it the users that you want to use the LightScribe software. THEN install the apps. After that, you won't need to run the applications as root. 

Here's how (substitute yourusername with your actual username):

# sudo -s
[enter your password when prompted]
# addgroup wheel
# adduser yourusername wheel
[repeat as necessary for all users you want to use the Lightscribe drive]

The re-install the packages.


Also, there's a typo in the path to one of the packages, so installation may hang unexpectedly. If it doesn't hang, it will at least give you problems, now or in the future. Here's how to fix:

Open a terminal or console and become root.
# sudo -s
[enter password when prompted]
# mv /usr/share/doc/lightscribeLicense.rtf.gz /usr/share/doc/lightscribe/License.rtf.gz 
# cd /usr/share/doc/[COLOR="Red"]lightscribe/[/COLOR]
# gunzip License.rtf.gz
# ln -s License.rtf /usr/share/doc/lightscribeLicense.rtf

Then reinstall. After the reinstall, run the following (still as root):

# cd /usr/share/doc/
# rm lightscribeLicense.rtf
# mandb
# exit

Happy Trails,

Loye Young
[http://www.iycc.biz](http://www.iycc.biz)
Laredo, Texas

---

### Post by J-Red on 2007-07-02
I can't even get my lightscribe drive recognized by my laptop in Ubuntu. 

Heres my post about it : [http://ubuntuforums.org/showthread.php?p=2951300#post2951300](http://ubuntuforums.org/showthread.php?p=2951300#post2951300)

Please, can anyone help me? I'm single booting right now but if I can't use the CD drive I might have to install a small vista partition ](*,)

---

### Post by reiki on 2007-07-11
> **bennyj said:**
> Has anyone checked out this [http://www.lightscribe.com/downloadsection/pse/index.aspx?campaign=1573&recipient=779800&link=download2]("http://www.lightscribe.com/downloadsection/pse/index.aspx?campaign=1573&recipient=779800&link=download2")

It has 2 packages for linux.you will need to install the Lss package first then install the simpleLabeler package.After installation you can find the luancher in /opt/lightscribeApplications/.From there you can just add it  to your menu.

Hope this helps

I uninstalled my previous 4L-gui and LSS and installed these 2 packages. It's a very simple install and, as you said, you have to manually add the launcher to a menu (or desktop). HOWEVER, this new evaluation software does NOT give me the ability to add my own background. No "outer ring" graphics. Just inner ring and some text. 

Still.... it seems to work quite well and was easy to install. If you ONLY want to do simple labels, this works.

---

### Post by maxim_86ualb2 on 2007-07-11
> **reiki said:**
> I uninstalled my previous 4L-gui and LSS and installed these 2 packages. It's a very simple install and, as you said, you have to manually add the launcher to a menu (or desktop). HOWEVER, this new evaluation software does NOT give me the ability to add my own background. No "outer ring" graphics. Just inner ring and some text. 

Still.... it seems to work quite well and was easy to install. If you ONLY want to do simple labels, this works.

I just create my label via the GIMP and save it as a png. Then write it onto the disk... works pretty well for me.

---

### Post by reiki on 2007-07-11
> **maxim_86ualb2 said:**
> I just create my label via the GIMP and save it as a png. Then write it onto the disk... works pretty well for me.

That works when you use 4L-gui, but the newest version of the lightscribe application does not give you an option of setting a background.

---

### Post by maxim_86ualb2 on 2007-07-11
> **reiki said:**
> That works when you use 4L-gui, but the newest version of the lightscribe application does not give you an option of setting a background.

Then use the old one.

---

### Post by Keen101 on 2007-07-13
ok, so what I gather is that it works fine in 7.04 feisty , right?


also, do you think it will work with the new gutsy gibbon coming out soon?


thanks,
-keen101

---

### Post by bennyj on 2007-07-13
> **Keen101 said:**
> ok, so what I gather is that it works fine in 7.04 feisty , right?


also, do you think it will work with the new gutsy gibbon coming out soon?


thanks,
-keen101

Works fine for me on Fiesty.not sure about Gusty

---

### Post by Evo8 on 2007-07-15
This looks like good news...

[URL="http://www.lightscribe.com/downloadSection/linux/index.aspx?id=816"][COLOR="Red"][SIZE="3"]LINUX PUBLIC SOFTWARE DEVELOPMENT KIT (SDK)[/SIZE][/COLOR]
05 July, 2007[/URL]

---

### Post by Keen101 on 2007-07-19
I can now confirm that it works fine for me in feisty!


Yeah lightscribe!


But, it would be nice to have a package made exclusively for Debian.  (and not have to use alien)


-keen101

---

### Post by WestCoastSuccess on 2007-08-08
Has anyone managed to get LIghtscribe working on an amd64? If so, could you post step-by-step instructions dumbed down for the likes of me? :)

I tried setting up a chroot environment but something went off the rails somewhere along the line...

Thanks!

---

### Post by loyeyoung on 2007-08-08
> I tried setting up a chroot environment

**THAT IS A SECURITY RISK AND A BAD IDEA**

I don't have an AMD64, but your processor should have little to do with installing the software.

I have posted this before, but I'll post it again because it may be difficult to find (thanks to maxim_86ualb2 for catching my mistake):

**[SIZE="4"]BEFORE INSTALLING THE LIGHTSCRIBE SOFTWARE[/SIZE]**, create a user group called "wheel", and add to it the users that you want to use the LightScribe software. THEN install the apps. After that, you won't need to run the applications as root. 

Here's how (substitute yourusername with your actual username):

# sudo -s
[enter your password when prompted]
# addgroup wheel
# adduser yourusername wheel
[repeat as necessary for all users you want to use the Lightscribe drive]

The re-install the packages.


Also, there's a typo in the path to one of the packages, so installation may hang unexpectedly. If it doesn't hang, it will at least give you problems, now or in the future. Here's how to fix:

Open a terminal or console and become root.
# sudo -s
[enter password when prompted]
# mv /usr/share/doc/lightscribeLicense.rtf.gz /usr/share/doc/lightscribe/License.rtf.gz 
# cd /usr/share/doc/lightscribe
# gunzip License.rtf.gz
# ln -s License.rtf /usr/share/doc/lightscribeLicense.rtf

Then reinstall. After the reinstall, run the following (still as root):

# cd /usr/share/doc/
# rm lightscribeLicense.rtf
# mandb
# exit

If you have problems, post back to this thread and let us know.

Happy Trails,

Loye Young
Isaac & Young Computer Company
[http://www.iycc.biz](http://www.iycc.biz)
Laredo, Texas

---

### Post by phantaszm on 2007-08-16
Not sure if this has already been posted, but it looks like they have a pre-release section that has deb packages

[http://www.lightscribe.com/downloadsection/pse/](http://www.lightscribe.com/downloadsection/pse/)

---

### Post by j_dog on 2007-08-26
> **reiki said:**
> For FEISTY users (I have not tried this in Edgy or Dapper or anything else)

I have the Lightscribe System Software as a .deb [here]("http://www.yardbird.net/lightscribe/lightscribe_1.6.45.1-0_i386.deb") 
This is lightscribe_1.6.45.1.rpm turned into a .deb using alien -k-c.
You need to install that one first.

Then I have the Lightscribe Labeler [here]("http://www.yardbird.net/lightscribe/4l_1.0-r6_i386.deb")
Install that one second.

You still have to run 4L as sudo so to start it:

sudo 4L-gui

Otherwise you won't be able to print (burn the lightscribe image to the media)

I'll leave those up as long as I don't have bandwidth problems from doing so :)

I sure would like to see someone post a 64 bit deb. I don't seem to be getting any where with the rpm.

---

### Post by kruppe on 2007-08-29
> **WestCoastSuccess said:**
> Has anyone managed to get LIghtscribe working on an amd64? If so, could you post step-by-step instructions dumbed down for the likes of me? :)

I tried setting up a chroot environment but something went off the rails somewhere along the line...

Thanks!

Please let me know. I'm also on AMD64 - have been reading loads of threads. Can't seem to get things to work.

---

### Post by longshanks197 on 2007-08-29
Lightscribe on AMD64 using the ia32-lib package. 

First off, I'm not an ubuntu user so stuff in here will not be exact (ie package names)
I use debian unstable but for the extra i386 libraries i went with etch packages for some reason.
This was just one of the first forums that I found that was really on topic and helped me so I'm trying to give back :)

I had ia32-libs and ia32-libs-gtk installed prior to this install. I then installed the two deb packages from:

[http://www.lightscribe.com/downloadSection/pse/](http://www.lightscribe.com/downloadSection/pse/)

using the following commands:

 dpkg -X lightscribe-1.8.15.1-linux-2.6-intel.deb /emul/ia32-linux/
 dpkg -X lightscribeApplications-1.8.11.0-linux-2.6-intel.deb /emul/ia32-linux/

This gives you the SimpleLabeler in:

/emul/ia32-linux/opt/lightscribeApplications/SimpleLabeler/
./SimpleLabeler

In order to get the labeler to recognize the lightscribe system software you need to either symlink or copy the /emul/ia32-linux/etc/lightscribe.rc file to /etc (I chose to symlink it)
and edit it to resemble the following:

ResourceDir=/emul/ia32-linux/usr/lib/lightscribe/res;
UpdateScriptDir=/emul/ia32-linux/usr/lib/lightscribe/updates;

The SimpleLabeler required me to add some other i386 libraries in order to run:

dpkg -X libpng3_1.2.15~beta5-1_all.deb /emul/ia32-linux/
dpkg -X libqt4-core_4.2.1-2+etch1_i386.deb /emul/ia32-linux/
dpkg -X  libqt4-gui_4.2.1-2+etch1_i386.deb /emul/ia32-linux/

I thought the simplelabeler kinda sucked so I wanted to try the LaCie labeler but couldn't make the deb package from the rpm on the amd64 system. Enter the following post:

> **reiki said:**
> For FEISTY users (I have not tried this in Edgy or Dapper or anything else)

I have the Lightscribe System Software as a .deb [here]("http://www.yardbird.net/lightscribe/lightscribe_1.6.45.1-0_i386.deb") 
This is lightscribe_1.6.45.1.rpm turned into a .deb using alien -k-c.
You need to install that one first.

Then I have the Lightscribe Labeler [here]("http://www.yardbird.net/lightscribe/4l_1.0-r6_i386.deb")
Install that one second.

You still have to run 4L as sudo so to start it:

sudo 4L-gui

Otherwise you won't be able to print (burn the lightscribe image to the media)

I'll leave those up as long as I don't have bandwidth problems from doing so :)

I downloaded the 4L labeler from the above post and installed it with:
dpkg -X 4l_1.0-r6_i386.deb /emul/ia32-linux/

cd /emul/ia32-linux/usr/bin
sudo ./4L-gui

...and enjoy lightscribe on an amd64 machine! I know it's not native but technically neither is my flash player so I can't complain. Hopefully we will get a native build in the near future. Let me know if this works for anyone else.

---

### Post by Jeff_From_VA on 2007-09-02
longshanks197 -- Thanks for that post!!   I got the lacie app up and working via your post.   Just wrote a disk fine, it looks real nice.

Couldn't get the other one working right, by your instructions for some reason, but I don't really care as I prefer the lacie app as it lets you use images....

---

### Post by Zeddicus Zorander on 2007-09-19
Looks like the [link]("http://download.lightscribe.com/ls/lightscribeApplications-1.8.11.0-linux-2.6-intel.deb") to download the Debian version of Simple Labeler is broken. Does anyone have an alternate location I can download this file from? Thanks! :)

---

### Post by WestCoastSuccess on 2007-09-21
Longshanks197: thank you, thank you, thank you! Finally: clear, concise instructions! I'd given up on this entirely a couple of weeks ago - just happened to be bored, so checked this thread again - following your instructions, for the first time, lightscribe recognizes my drive! Gotta go...there's burnin' to be done!

---

### Post by WestCoastSuccess on 2007-09-21
PS: ZZ: why not just use the lightscribe labeler? There's a link to the deb in longshank's post, in the box towards the end...the simplelabeler link didn't work for me either...

---

### Post by Didjit on 2007-09-23
> **longshanks197 said:**
> Lightscribe on AMD64 using the ia32-lib package. 



I tried this with the 4L and it says no drives are found. 

Is there something else that needs to be installed outside this post?
 
Thank you,

Didjit
**Edit: Not sure what I missed. Has lib loading errors, this fixed it: sudo cp /emul/ia32-linux/usr/lib/liblightscribe.so.1 /usr/lib32/liblightscribe.so.1**

---

### Post by longshanks197 on 2007-09-24
Thanks to all who replied and let me know how you all made out. Good to hear that my instructions were somewhat coherent. Jeff_from_Va, I'm with you on the Simplelabeler, I'm sure we could figure out how to get it working (one thing i missed is that you need to sudo to get it to write..haven't worked on getting to work with permissions changes) but it's really not worth it. Zeddicus, not sure what to tell you about the hp.com link other than I had a copy before it broke and uploaded it to one of those free hosting sites:

[Download lightscribeApplications-1.8.11.0-linux-2.6-intel.deb](http://www.filecrunch.com/file/~1j16cu)

Hopefully that gets you going.

Didjit, I'm assuming that by copying the files over you are up and running? Not sure how or why your system is different but my system has /usr/lib32/ symlinked to /emul/ia32-linux/usr/lib/

I'm going to plead ignorance on why that is, not sure if it's a ia32-libs deal or what. I would probably recommend that you put the libraries in /emul/ia32-linux/usr/lib/ and fix the symlink because that makes more sense...to me at least... Really, it's your call as it's your system. 

Well to Westcoast, Jeff, Didjit and hopefully Zeddicus, too, good to hear things are working and I'll stop back in and see if there is anything else I can try and help with. I was really excited that it worked myself. I was reading of others using a dpkg -i --force-architecture <file>.deb and getting the stuff to install but that seems really messy to me (having the executables mixed). Anyway, Cheers!

---

### Post by Didjit on 2007-09-25
> **longshanks197 said:**
> 
Didjit, I'm assuming that by copying the files over you are up and running? 

Yep, I'm up. Thanks.

Didjit

---

### Post by GavinZac on 2007-10-06
> **longshanks197 said:**
> Thanks to all who replied and let me know how you all made out. Good to hear that my instructions were somewhat coherent. Jeff_from_Va, I'm with you on the Simplelabeler, I'm sure we could figure out how to get it working (one thing i missed is that you need to sudo to get it to write..haven't worked on getting to work with permissions changes) but it's really not worth it. Zeddicus, not sure what to tell you about the hp.com link other than I had a copy before it broke and uploaded it to one of those free hosting sites:

[Download lightscribeApplications-1.8.11.0-linux-2.6-intel.deb](http://www.filecrunch.com/file/~1j16cu)

Hopefully that gets you going.

Didjit, I'm assuming that by copying the files over you are up and running? Not sure how or why your system is different but my system has /usr/lib32/ symlinked to /emul/ia32-linux/usr/lib/

I'm going to plead ignorance on why that is, not sure if it's a ia32-libs deal or what. I would probably recommend that you put the libraries in /emul/ia32-linux/usr/lib/ and fix the symlink because that makes more sense...to me at least... Really, it's your call as it's your system. 

Well to Westcoast, Jeff, Didjit and hopefully Zeddicus, too, good to hear things are working and I'll stop back in and see if there is anything else I can try and help with. I was really excited that it worked myself. I was reading of others using a dpkg -i --force-architecture <file>.deb and getting the stuff to install but that seems really messy to me (having the executables mixed). Anyway, Cheers!

That link is giving me a file which wont open, it says its "corrupted or check permissions". I've openned it as sudo and got the same results. I've downloaded it twice to check if it was just a bad download but same result.

---

### Post by j_dog on 2007-10-06
Yup,  me too !:confused:

---

### Post by GavinZac on 2007-10-06
> **j_dog said:**
> Yup,  me too !:confused:

I just downloaded the .rpm and used alien to convert it to .deb

not ideal, but worked well enough :)

---

### Post by longshanks197 on 2007-10-07
Using alien is perfectly okay, that's what it's there for. The problem is for people using amd64 because it doesn't want to do the conversion. Probably could do the conversion if you setup a chroot but that is a huge pain. As far as the download being corrupt, I'm not sure what to tell you other than, did you check the permissions? ls -la should give you a file size of 7028210 and the user and group should be owned by your account. My file has permissions of 644.  I redownloaded the file and I was able to dpkg -X lightscribeApplications-1.8.11.0-linux-2.6-intel.deb and open it with no problems. The following is an md5 checksum of the file:

69ec30e6bdf9d104a50fd5e9e4a63835  lightscribeApplications-1.8.11.0-linux-2.6-intel.deb

Copy that text to a file and put it in the same directory as the downloaded deb package and run:

md5sum --check <md5 file>

And it should check out. If not let me know.

---

### Post by reiki on 2007-10-20
the problem people are having with your file is that it is the deb created from the rpm. There is a group "wheel" that ubuntu does not have and it's referred to in all the files inside that deb. The workaround might be to add the group "wheel" and then add themselves and root to that group.

---

### Post by jdfreshwater on 2007-10-20
Got a labler working in AMD 64 branch.  First I downloaded Debs from [http://lightscribe.com/downloadSection/pse/]("http://lightscribe.com/downloadSection/pse/") .
Next I did an isntall with sudo dpkg -i -force architecture <both pkgs>.

You must install either Dolphin or Konquoror in order for the program to work.

Run the command  /opt/lightscribeApplications/SimpleLabeler/./SimpleLabeler  .  

You should now Have a simple way to Add text to the Disc.

---

### Post by loyeyoung on 2007-10-21
> **reiki said:**
> the problem people are having with your file is that it is the deb created from the rpm. There is a group "wheel" that ubuntu does not have and it's referred to in all the files inside that deb. The workaround might be to add the group "wheel" and then add themselves and root to that group.

See my post above at [http://ubuntuforums.org/showpost.php?p=3153977&postcount=135](http://ubuntuforums.org/showpost.php?p=3153977&postcount=135). 

**DO NOT ADD ROOT TO THE WHEEL GROUP. ** Root already has super powers and should never be added to other groups. Because other programs sometimes use group membership  you might be bootstrapping interaction with root that is unexpected. 

Loye Young
Isaac & Young Computer Company 
Laredo, Texas
[http://www.iycc.biz](http://www.iycc.biz)

---

### Post by reiki on 2007-10-22
> **loyeyoung said:**
> See my post above at [http://ubuntuforums.org/showpost.php?p=3153977&postcount=135](http://ubuntuforums.org/showpost.php?p=3153977&postcount=135). 

**DO NOT ADD ROOT TO THE WHEEL GROUP. ** Root already has super powers and should never be added to other groups. Because other programs sometimes use group membership  you might be bootstrapping interaction with root that is unexpected. 

Loye Young
Isaac & Young Computer Company 
Laredo, Texas
[http://www.iycc.biz](http://www.iycc.biz)

Good catch. My error. You simply need to add yourself to the wheel group... no need to add root. (I have no idea what I was thinking when I typed that) 

:D

---

### Post by loyeyoung on 2007-10-22
"I  have no idea what I was thinking "

Watchin' your back, reiki. Party on, my friend.

:-D

Loye

---

### Post by Jott on 2007-10-22
I'm a little lost and hoping for some help.  I'm running gutsy 64 bit and would love to get lightscribe working.  I more or less followed Longshanks guide, but I don't have a /emul/* directory.  I ran the dpkg -X command with /usr/lib32/ as the directory (not really sure why, seemed like a good idea at the time).  That just gave me a list of stuff.  I tried installing the lightscribe and the 4l debs with --force-architecture.  after that the 4l-gui works, but no drive is detected.  It gave me this error:\

 4L-cli: error while loading shared libraries: liblightscribe.so.1: cannot open shared object file: No such file or directory

I saw that someone else had posted a similar issue, and solved it by copying the file to the proper directory.  I seem to have neither the file nor the directory.  I also have no real idea what I'm doing, as is probably obvious by now.  I would really like to get this to work though, if anyone has any ideas.

Thanks!

---

### Post by hobbes_ba on 2007-10-23
Hi, i' m trying to download the [**Simple Labeler Debian Install Package (6.7 MB)**]("http://download.lightscribe.com/ls/lightscribeApplications-1.8.11.0-linux-2.6-intel.deb") today and so far no sucess.

It keeps me saying: We're very sorry! The file you are attempting to download is not available at this time. Please try again later or contact our customer support at  [email]ebusinesssupport@hp.com[/email] to resolve this issue by providing complete order information and your contact details.

I' m wondering if anyone here at the Ubuntu  Forums has this .deb package to share?

I had just bought and External DVD Burner with Lightscribe support and i want to try it out.

Anyone?

---

### Post by reiki on 2007-10-23
for anyone trying to activate the enhanced contrast setting and getting errors, EDIT THE FILE. They didn't put #! bin/bash as the first line. I added that and it ran perfectly.

Instructions are to run this:
sudo /usr/lib/lightscribe/elcu.sh

edit elcu.sh and it will work.

---

### Post by longshanks197 on 2007-10-23
Wow, this thread got really busy all of a sudden. Like I stated up front on my initial post I'm really a Debian Sid user, however, it should be really close to the ubuntu releases. I'm going to try and answer the previous posts and some of the newer ones. First up:

> **Jott said:**
> I'm a little lost and hoping for some help.  I'm running gutsy 64 bit and would love to get lightscribe working.  I more or less followed Longshanks guide, but I don't have a /emul/* directory.  I ran the dpkg -X command with /usr/lib32/ as the directory (not really sure why, seemed like a good idea at the time).  That just gave me a list of stuff.  I tried installing the lightscribe and the 4l debs with --force-architecture.  after that the 4l-gui works, but no drive is detected.  It gave me this error:\

 4L-cli: error while loading shared libraries: liblightscribe.so.1: cannot open shared object file: No such file or directory

I saw that someone else had posted a similar issue, and solved it by copying the file to the proper directory.  I seem to have neither the file nor the directory.  I also have no real idea what I'm doing, as is probably obvious by now.  I would really like to get this to work though, if anyone has any ideas.

Thanks!

My guide starts with the assumption that  ia32-libs and ia32-libs-gtk packages are installed already. The libs packages is going to provide /emul/.

If you installed with the --force-architecture you should have liblightscribe.so.1 in /usr/lib/. You may have to run ldconfig (use sudo ldconfig) but check if the file is there first. First way to verify is check /usr/lib. If it isn't and your locate cache is up to date you can run `locate liblightscribe` if not run `cd / ; find -name "liblightscribe*"`(it will take a while to run). 

Just a note, dpkg -X will unpack the package and will not run any installation scripts and will not show that it is installed (you cannot apt-get remove the package).

Let me know if this helps you at all. Unfortunately, without a native 64bit package it's not a straight forward installation.

Next:

hobbes_ba, I tried to repost that package (post #145 of this thread) though some people are saying it doesn't work. Reiki indicated that it has to do with the wheel group, though I'm not convinced this is the case. (I run debian, the distribution of which ubuntu is based, and also do not have a wheel group) I downloaded the file from HP  before the file went missing and still had a copy so I threw it up on a site. I was able to redownloaded it and put the MD5 checksum of the downloaded file in post #150. I was able to run dpkg -X on it and it opened fine. If this file still doesn't work let me know.

It may be wise to look at Loye Young's post (#135) regarding the wheel group prior to installing the software. I haven't gone back and reinstalled to verify it nor have I used the --force-architecture option of installation. I've just been busy with work and other things to make my lightscribe installation better. My initial post was step by step instructions of how I got my installation to work and may not work for everyone and probably isn't the "best way".  Hopefully this helps out some people and I'll probably check back in later and cause more problems. Cheers!

---

### Post by Jott on 2007-10-23
I think I got it to work.  I used the dpkg -x command and unpacked everything into /usr/lib32/ - I don't really know why.  I think it was because it looked like that was where the lib32 packages were - a bunch of them got installed when I used a script to set up the 32bit firefox.  I ended up putting symlinks for lightscribe.so.1 into a couple of places that seemed likley for the the 4l-gui to look for it in; I think the one that worked was /usr/lib/.  I also put one in /etc/, just for the record.  Anyway, when I ran 4l-gui as root it found my drive and looks like it will work.  I have to get a lightscribe disc to test (didn't know I needed special discs), but it looks pretty hopeful.

Thanks for all your help, I'm excited to see this work!

---

### Post by reiki on 2007-10-24
I emailed lightscribe.com from a feedback link and told them that the link to the Simple Labeler was broken. They responded that there is an equipment issue preventing them from fixing it immediately, and they attached both the lightscribe system files installer as well as the lightscribe simple labeler to an email back to me. 

As of this morning, that link is still broken. I have the files on my web server and will give you a URL if you PM me. I just don't want to publish the URL here on the boards as I don't want to see my bandwidth get clobbered. If that starts to happen I will be forced to take them down so please don't share the URL once I've given it to you.

You can also just send feedback to to lightscribe.com using their Support link and they'll send you the most recent files. (in case you are reluctant to download files from someone you don't know... which I completely respect).

the version on the files they sent me is 1.10.13.1 for both files. I have installed them on Gutsy and they work fine.

I haven't install the 4L application from LaCie yet on Gutsy. I still have a Feisty install with 4L working perfectly. I like the fact that 4L can do full disk backgrounds.

---

### Post by hobbes_ba on 2007-10-24
> **longshanks197 said:**
> 

hobbes_ba, I tried to repost that package (post #145 of this thread) though some people are saying it doesn't work. Reiki indicated that it has to do with the wheel group, though I'm not convinced this is the case. (I run debian, the distribution of which ubuntu is based, and also do not have a wheel group) I downloaded the file from HP  before the file went missing and still had a copy so I threw it up on a site. I was able to redownloaded it and put the MD5 checksum of the downloaded file in post #150. I was able to run dpkg -X on it and it opened fine. If this file still doesn't work let me know.

It may be wise to look at Loye Young's post (#135) regarding the wheel group prior to installing the software. I haven't gone back and reinstalled to verify it nor have I used the --force-architecture option of installation. I've just been busy with work and other things to make my lightscribe installation better. My initial post was step by step instructions of how I got my installation to work and may not work for everyone and probably isn't the "best way".  Hopefully this helps out some people and I'll probably check back in later and cause more problems. Cheers!


Thanks for replying, i tried to download without success, but i just received a PM with a link from reiki.

You can find more details on the post  #161

Thanks again, for replying.

---

### Post by hobbes_ba on 2007-10-24
> **reiki said:**
> for anyone trying to activate the enhanced contrast setting and getting errors, EDIT THE FILE. They didn't put #! bin/bash as the first line. I added that and it ran perfectly.

Instructions are to run this:
sudo /usr/lib/lightscribe/elcu.sh

edit elcu.sh and it will work.

Just helping you out, you forgot to put the first "/" before "bin".

So, the right way to make this work is:

EDIT THE FILE: gksu gedit /usr/lib/lightscribe/elcu.sh

ADD ON THE VERY FIRST LINE: #!/bin/bash

It will look like this:

#!/bin/bash
# Define path to LightScribe installation
lspath=/usr/lib/lightscribe

_____________________________________________

Have fun!

---

### Post by reiki on 2007-10-24
thanks for watchin' my back. Seems to be happening more and more. The older I get, the more the old rememberer ain't rememberin'

:)

---

### Post by hobbes_ba on 2007-10-25
Hi folks, i have a doubt. I Just received today some DVDs with lightscibe and finally I tested it. 

I have a question: Can I burn twice a DVD Lightscribe?

I burned a DVD with a PBS Special about The American Revolution, so i put it "The American Revolution" on Top label and at the bottom label PBS, but the final result i found to be too clear, too lighter, i just want to make this a little bit darker.

It is possible to burn a DVD lightscribe again? The Burner will recognize the exact same spot to re-write over?

Anyone?

---

### Post by j_dog on 2007-10-25
Yes, a second time will darken it.

---

### Post by deuce868 on 2007-10-25
> **reiki said:**
> I emailed lightscribe.com from a feedback link and told them that the link to the Simple Labeler was broken. They responded that there is an equipment issue preventing them from fixing it immediately, and they attached both the lightscribe system files installer as well as the lightscribe simple labeler to an email back to me. 

As of this morning, that link is still broken. I have the files on my web server and will give you a URL if you PM me. I just don't want to publish the URL here on the boards as I don't want to see my bandwidth get clobbered. If that starts to happen I will be forced to take them down so please don't share the URL once I've given it to you.


If you want I have a colo server on a fat pipe that can host the files for now and we can just put the url in the thread. My lightscribe dvd burner should be showing up tomorrow so I'm psyched to try this out. 

Feel free to email me at the address in my launchpad:
[https://launchpad.net/~rharding](https://launchpad.net/~rharding)

Thanks

---

### Post by hobbes_ba on 2007-10-25
> **j_dog said:**
> Yes, a second time will darken it.

Thanks for replying.

So if you burn twice the text will be lined up in the exact same spot? ? I forgot to mention that i took the DVD off the driver to put on my DVD standalone to check if everything was playing well...

It will work?

---

### Post by hobbes_ba on 2007-10-25
> **hobbes_ba said:**
> Thanks for replying.

So if you burn twice the text will be lined up in the exact same spot? ? I forgot to mention that i took the DVD off the driver to put on my DVD standalone to check if everything was playing well...

It will work?

YES, IT WORKS! :)

And here is why:

**[LightScribe Discs]("http://www.backupcritic.com/faq/lightscribe/discs/")**

LightScribe discs are specially constructed on the "label side" in order to allow a LightScribe drive laser to burn a precise image. A thin dye layer on that side lets the laser burn graphical images with the same laser that burned data on the other side (at a much higher speed, most likely!).

The hub of a LightScribe disc contains special calibration marks so that the drive can accurately obtain the disc's rotation at any given point in time. This is why you can actually burn the same image into the same LightScribe disc twice, and the second burn will precisely land right on top of the first one. 

- - - - - - - - - - - - - - 

Lightscribe is getting better by the minute!

Hope that help someone else!

Have fun!

---

### Post by deuce868 on 2007-10-26
It might take a little bit for the DNS to propagated, but the files are located here:

[http://uploads.mitechie.com/lightscribe/](http://uploads.mitechie.com/lightscribe/)

I just setup the subdomain this morning though so don't be surprised if it takes a day for the dns to resolve. 

Feel free to grab any of the lightscribe files there and let me know if you run into any issues.

---

### Post by reiki on 2007-10-26
> **deuce868 said:**
> It might take a little bit for the DNS to propagated, but the files are located here:

[http://uploads.mitechie.com/lightscribe/](http://uploads.mitechie.com/lightscribe/)

I just setup the subdomain this morning though so don't be surprised if it takes a day for the dns to resolve. 

Feel free to grab any of the lightscribe files there and let me know if you run into any issues.

Working already here. By the way if those 4L files are from my server, they *may* not be the most current versions. I haven't installed 4L in a while. I have also found the files from Lacie (the 4L application) are not updated as often as the ones from lightscribe.com 

Of the 4 files showing, if you just install the ones with 1.10.13.1 in the filename, you're installing the lightscribe simple labeler from lightscribe.com. With those 2 files you want to install the one that says "lightscribe" FIRST (that's important) and teh one that says "lightscribeApplications" SECOND.

**EDIT ** and as of this morning, the link from lightscribe.com is still broken. So thank you to deuce868 for hosting the files while that gets straightened out. :)

---

### Post by OnSite511 on 2007-10-27
I want to thank you for hosting those files. I do have question though. Assuming that I've installed them properly, where would the applications be? I've looked in the main menu, but I've yet to find them. Its always possible I've done something wrong.

thanks

---

### Post by reiki on 2007-10-27
> **OnSite511 said:**
> I want to thank you for hosting those files. I do have question though. Assuming that I've installed them properly, where would the applications be? I've looked in the main menu, but I've yet to find them. Its always possible I've done something wrong.

thanks

create a launcher that uses this command:

/opt/lightscribeApplications/SimpleLabeler/SimpleLabeler

done! :)

---

### Post by reiki on 2007-10-27
Ok I've also converted the Lacie 4L application from an .rpm to a .deb and tested it on my own machine. Works great! I've uploaded the new 4L application to my web server and hopefully deuce868 will be kind enough to grab it and host it with the other 2 files. 

The files should be installed in this order:
lightscribe-1.10.13.1-linux-2.6-intel.deb
lightscribeApplications-1.10.13.1-linux-2.6-intel.deb
4l_1.0-r6_i386.deb

The difference between lightscribe.com's Simple Labeler and Lacie's 4L application is that the 4L application lets you choose an image for a full background of a disk. You don't type text into it. So you make an image and then you use that entire image as a background. These typically take longer to burn because it's the entire disk surface. Lightscribe burns images in concentric circles.

I think I have a template for Gimp for making CD labels. It works great for making the images for a lightscribe burn. I'll try and find it.

Lightscribe Simple Labeler (from lightscribe.com) runs when you create a launcher on your desktop or in your menu that uses this command:
/opt/lightscribeApplications/SimpleLabeler/SimpleL abeler

Lacie's 4L application can be started from a launcher that simply says:
4L-gui  (yes, it's case sensitive)

---

### Post by deuce868 on 2007-10-27
> **reiki said:**
> Ok I've also converted the Lacie 4L application from an .rpm to a .deb and tested it on my own machine. Works great! I've uploaded the new 4L application to my web server and hopefully deuce868 will be kind enough to grab it and host it with the other 2 files. 


Updated

---

### Post by reiki on 2007-10-27
deuce868-

I also just uploaded the lightscribe_template.gif if you want to grab that as well.
Works in Gimp

---

### Post by deuce868 on 2007-10-27
> **reiki said:**
> deuce868-

I also just uploaded the lightscribe_template.gif if you want to grab that as well.
Works in Gimp

Thanks, I put it up. I was thinking if you were really motivated and wanted to put together a README.txt from your posts in this thread that might be cool to put in there as well.

---

### Post by reiki on 2007-10-27
> **deuce868 said:**
> Thanks, I put it up. I was thinking if you were really motivated and wanted to put together a README.txt from your posts in this thread that might be cool to put in there as well.

OK... README.TXT is on my web server if you want to grab it and take a look.

---

### Post by deuce868 on 2007-10-28
> **reiki said:**
> OK... README.TXT is on my web server if you want to grab it and take a look.

Sorry, not seeing it.

---

### Post by OnSite511 on 2007-10-28
So I just tried to install the lacie 4L deb on my Fiesty Fawn (7.04) distro and it errors out complaining: '**[COLOR="Red"]Error" Dependency is not satisfiable: libc6[/COLOR]**', but I've got libc6 ver. 2.5-0ubuntu14 . Is there a specific version I need ?

thanks

---

### Post by reiki on 2007-10-28
> **deuce868 said:**
> Sorry, not seeing it.

Not sure why it's not showing in the list, but if you go to  mywebsite/lightscribe/README.TXT it comes up

Same with teh template
mywebsite/lightscribe/lightscribe_template.gif

it comes up in the browser

---

### Post by reiki on 2007-10-28
> **OnSite511 said:**
> So I just tried to install the lacie 4L deb on my Fiesty Fawn (7.04) distro and it errors out complaining: '**[COLOR="Red"]Error" Dependency is not satisfiable: libc6[/COLOR]**', but I've got libc6 ver. 2.5-0ubuntu14 . Is there a specific version I need ?

thanks

Did you install the lightscribe system files first?
That'd be this one:
lightscribe-1.10.13.1-linux-2.6-intel.deb

That file has to be installed in order to get any of the actual lightscribe apps to work.

---

### Post by deuce868 on 2007-10-28
> **reiki said:**
> Not sure why it's not showing in the list, but if you go to  mywebsite/lightscribe/README.TXT it comes up

Same with teh template
mywebsite/lightscribe/lightscribe_template.gif

it comes up in the browser

Ok, thanks, got it up on there. Not sure why it didn't list, but the direct link worked out ok.

---

### Post by OnSite511 on 2007-10-28
Yep, I just uninstalled all lightscribe packages, then reinstalled them in the specified order and I still get the error when I attempt to install the 4L package.

---

### Post by reiki on 2007-10-29
> **OnSite511 said:**
> Yep, I just uninstalled all lightscribe packages, then reinstalled them in the specified order and I still get the error when I attempt to install the 4L package.

Let me take a look at this. The 4L package was turned into a .deb using alien. It's possible when we convert it that it's referencing your installed libc6 libraries. 

Meanwhile if you would like to help out a bit here (or anyone else with Feisty) I have something you can try. 

Go to [http://www.yardbird.net/lightscribe/4L](http://www.yardbird.net/lightscribe/4L)
You should see a single file there named 4L-1.0-r6.i586.rpm
Get that file.

Now I'd like you to use alien to convert it to a .deb on your Feisty install

If you don't have alien installed, it is available in the repos so you should be able to simply
```
sudo apt-get install alien
```

Once you have alien you can convert the rpm to a deb by using
```
sudo alien -k 4L-1.0-r6.i586.rpm
```

in a terminal. (Make sure you're in the directory where that rpm file is before issuing the command)

This should create a .deb file for you. 

See if that fixes the dependancy issue. If it does I'll have to adjust the README.TXT file and/or put up separate 4L install files for Feisty and Gutsy

---

### Post by OnSite511 on 2007-10-29
Sure thing. I'd love to help. When I get home tonight I'll do it and if it works, do you want me to post the deb it somewhere?

---

### Post by reiki on 2007-10-29
> **OnSite511 said:**
> Sure thing. I'd love to help. When I get home tonight I'll do it and if it works, do you want me to post the deb it somewhere?

If converting it yourself works, then yes, sharing the .deb would be great. If you can host it, fine, and if not either deuce868 or myself can probably host it. Would probably be good to have all the files in one place anyways  instead of having people hop around looking for them.

On another note...

I am working on using Inkscape to create lightscribe labels before burning. I found it really hard to get The Gimp to do text on curves or paths. Inkscape does this, but I am learning how to make concentric circles and I want to have an easy way for people to build lightscribe labels using text on circles that conform to the disk media. I'm kinda new to inkscape. If I can get a basic template with a mask to show folks what will be visible on the lightscribe burn, that would be a start. It doesn't look HARD to use Inkscape, but as I said, it's new for me and I'm learning as I go. If I can get a decent result, I'm sure I can explain to others how to do the same.

---

### Post by Sciamano on 2007-10-29
> **loyeyoung said:**
> **THAT IS A SECURITY RISK AND A BAD IDEA**

I don't have an AMD64, but your processor should have little to do with installing the software.

I have posted this before, but I'll post it again because it may be difficult to find (thanks to maxim_86ualb2 for catching my mistake):

**[SIZE="4"]BEFORE INSTALLING THE LIGHTSCRIBE SOFTWARE[/SIZE]**, create a user group called "wheel", and add to it the users that you want to use the LightScribe software. THEN install the apps. After that, you won't need to run the applications as root. 

Here's how (substitute yourusername with your actual username):

# sudo -s
[enter your password when prompted]
# addgroup wheel
# adduser yourusername wheel
[repeat as necessary for all users you want to use the Lightscribe drive]

The re-install the packages.


Also, there's a typo in the path to one of the packages, so installation may hang unexpectedly. If it doesn't hang, it will at least give you problems, now or in the future. Here's how to fix:

Open a terminal or console and become root.
# sudo -s
[enter password when prompted]
# mv /usr/share/doc/lightscribeLicense.rtf.gz /usr/share/doc/lightscribe/License.rtf.gz 
# cd /usr/share/doc/lightscribe
# gunzip License.rtf.gz
# ln -s License.rtf /usr/share/doc/lightscribeLicense.rtf

Then reinstall. After the reinstall, run the following (still as root):

# cd /usr/share/doc/
# rm lightscribeLicense.rtf
# mandb
# exit

If you have problems, post back to this thread and let us know.

Happy Trails,

Loye Young
Isaac & Young Computer Company
[http://www.iycc.biz](http://www.iycc.biz)
Laredo, Texas

I already had a wheel group with myself in it.
I've downloaded the new LS programs and updated the old versions I had.
Still, 4L refuses to start printing, saying that it needs root privileges. :-(
Any suggestions?

---

### Post by stoodleysnow on 2007-10-29
OK, so where can I find .deb lightscribe packages for amd64?
:?::?:

---

### Post by OnSite511 on 2007-10-29
Ok, so I've converted the .rpm to a .deb and its @ [www.zabaronick.com/deb](www.zabaronick.com/deb)

It installed just fine. thanks.

---

### Post by reiki on 2007-10-30
> **OnSite511 said:**
> Ok, so I've converted the .rpm to a .deb and its @ [www.zabaronick.com/deb](www.zabaronick.com/deb)

It installed just fine. thanks.

To confirm..... when you got the rpm and converted it yourself using alien, it then works on your Feisty system fine. Correct?

Do you need to use root privs to run it? (do you need to start it with sudo?)

---

### Post by reiki on 2007-10-30
> **Sciamano said:**
> I already had a wheel group with myself in it.
I've downloaded the new LS programs and updated the old versions I had.
Still, 4L refuses to start printing, saying that it needs root privileges. :-(
Any suggestions?

find the 4L-gui program and check properties. What is the ownership and group?

---

### Post by Sciamano on 2007-10-30
> **reiki said:**
> find the 4L-gui program and check properties. What is the ownership and group?

Ownership is "luca" (my account)
Group is  "wheel"

Permissions are -rwxrwxr-x for both 4L-gui and 4L-cli

---

### Post by OnSite511 on 2007-10-30
> **reiki said:**
> To confirm..... when you got the rpm and converted it yourself using alien, it then works on your Feisty system fine. Correct?

Do you need to use root privs to run it? (do you need to start it with sudo?)

Correct, I converted the rpm to a deb on my Feisty system and then used the deb installer to install it.

I created an installer link in my sound and video grouping (Right click on main menu >edit menus >sound and video, click on new item. be aware the the new item opens below/behind the edit main menu dialog.)

enter 4l-gui for the command (case-sensitive) and you're all set.

---

### Post by j_dog on 2007-10-31
Maybe someone can put together a script for this ?:?

---

### Post by Hilko on 2007-11-09
This is how I got simple labeler and 4L (Lacie Lightscribe Labeler for Linux) working in Gutsy;

Go to [http://www.lightscribe.com/downloadsection/linux/index.aspx](http://www.lightscribe.com/downloadsection/linux/index.aspx) , download and install
lightscribe system software
lightscribe simple labeler.

This must be done in the above order. Choose the .Deb files, (not the .rpm). Installation instructions are given there, but it just comes down to downloading and double clicking on the downloaded files.

To install 4L, download 4l_1.0-r6_i386.deb from [http://uploads.mitechie.com/lightscribe/](http://uploads.mitechie.com/lightscribe/) and double click the downloaded file.

Add launchers on your panel;
for simple labeler use the command: /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler
for 4L use the command: 4L-gui

done.

The applications run fine, but I have not yet tested them by actually burning a label.

---

### Post by j_dog on 2007-11-09
This doesn't work for  64 bit. it tells me wrong achitecture .

---

### Post by Hilko on 2007-11-10
I just burned my First label ! and it worked !!! (I've tested both simple labeler and 4L)

The only thing is that one needs to run 4L with root priveleges. So in a terminal type:
```
$sudo 4L-gui
```

I have a 64 bit machine too, and don't seem to have any problems...

---

### Post by j_dog on 2007-11-10
I can't even install the software. it says wrong architecture.  :(

---

### Post by clubsoda on 2007-11-14
Although it's proprietary bloatware and I'm not accustomed to having advertisements appear on my linux machines, I'll give a tentative thumbs-up to the SimpleLabeler, mostly because it is fairly quick.  I'm guessing that the reason lightscribe is slow compared to burning a CD is that a label provides no pre-groove, hence all the timing has to be derived from the pulses being sent to the motor rotating the disc.  

Question: Does 4L burn quicker if the image is constrained within a certain radius, and if so, should the outer portion of the design be white to achieve this?

With only a handful of lightscribe discs burnt so far, the Simple Labels are working but some different coloured discs would certainly help.  I'm finding Verbatim CD-R discs burn cleanly but DVD+R discs by the same maker come out very fuzzy.

---

### Post by reiki on 2007-11-16
Lightscribe burns are indexed from the media, not the drive. If you look at the innermost ring of the media... right next to the center hole... you'll see marks. The Lightscribe media is indexed on those marks. This is what makes it possible for you to burn a lightscribe image TWICE (or more) even if you remove the media and put it back in.

> Question: Does 4L burn quicker if the image is constrained within a certain radius, and if so, should the outer portion of the design be white to achieve this?

Lightscribe burns in concentric circles. If you look at Simple Labeler you can choose upper text and lower text and you can choose a simple design as well if you want. If you then look at the preview, all of those elements are constrained within a "ring" on the media. In other words.... from the center of the media and moving out toward the edge....there is nothing to burn until you get about half way out and then it burns the contents of that "ring" and then there's nothing to burn all the way out to the edge. 

that type of label is very fast. My drive does them in about 2 and a half minutes.

Now take a look at 4L. You're bringing in an image. It *can* be an image that covers the entire surface of the media. Essentially that means the drive has to burn something in EVERY concentric ring from the center to the edge. Those burns on my drive can take 30 to 35 minutes and maybe more depending on what the image is. 

Should the outer portion be white? I don't think so but I've never tried this. I usually have areas I don't want burned as transparent in the image.

---

### Post by toobaz on 2007-12-09
> **j_dog said:**
> This doesn't work for  64 bit. it tells me wrong achitecture .

I hope you already solved, I'll write it here anyway: to install 32 bits packages in a 64 bit Ubuntu, do not use the graphic interface; just move to the directory where you dowloaded the package and give the command:

sudo dpkg -i --force-architecture nameofthepackagefile.deb

---

### Post by reiki on 2007-12-09
OK!  Using Inkscape I've made a template with instructions so that you can pull in a graphic, put text on a circular path, etc. All that neat stuff. It's a SIMPLE template. you can probably BREAK it so make a second copy to keep as a fresh one. It just uses layers and has some guides on it for placement and instructions for putting text on a path and ... well you'll see. 

I won't know if this is helpful unless people actually TRY it so feel free.. and let me know how this works out for you.

Not sure which attachment will work but here goes... they're the same thing but one is compressed for transport...

---

### Post by djfolsom on 2007-12-09
I hope this will help it is a site with drivers for light scrib for linux, ran across it in a review about 
linux against vista..[http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)    :cool::cool:

---

### Post by csamuel on 2008-01-05
> **go_dragons said:**
> Has anyone tried to do this with AMD64?

Yes - I'm running 4L-gui happily on KUbuntu Gutsy - I blogged about how I did it here:

[http://www.csamuel.org/2007/11/29/installing-lacie-4l-lightscribe-software-on-amd64-ubuntudebian-systems]("http://www.csamuel.org/2007/11/29/installing-lacie-4l-lightscribe-software-on-amd64-ubuntudebian-systems")

But the executive summary was that I used alien to convert both the .deb and .rpm into a tar file and then used alien to convert them back to .deb files.   :-)

---

### Post by esmerine on 2008-01-29
damn. i've just bought the 20A3H drive, installed debs from lightscribe.com, but saw that simple labeler cannot print full cds. installed lacie but getting error

```

4L-cli: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

when trying to open 4L-cli. or enumerate (when i want to enumerate, i just type 4L-cli enumerate?)
these things i was trying to do unluckily because lacie tells me that my drive is not detected. :[

Edit: there's the code of God:
```
sudo apt-get install libstdc++5
```

Terminal just tells you what to do, but if you're not experienced you might get lost or just type the wrong name.
/me happily printing dragons.

---

### Post by WestCoastSuccess on 2008-01-30
Check your permissions for libstdc++.so.5 (which should be in /usr/lib32) - mine are set to read/write/execute for all (tho you probably don't need write permission).

You can check like this:

#ls -l /usr/lib32/libstdc++.so.5

Mine shows:

#-rwx rwx rwx

To change the permissions, type:

#sudo chmod a+rwx /usr/lib32/libstdc++.so.5

Let me know if that solves your issue.

Cheers!

---

### Post by loyeyoung on 2008-01-30
@ esmerine

> Edit: there's the code of God:
Code:

sudo apt-get install libstdc++5

Suggestion: apt-get is deprecated upstream. Use aptitude instead of apt-get, which will by default install "Recommended" dependencies. Recommended dependencies are packages that are not strictly required for the subject package to be useful, but that enable functionality that would normally be expected (I'm paraphrasing the definition because I'm too lazy to look it up). 

As an added bonus, aptitude is much more sophisticated in its handling of dependencies when you want to remove packages. Your case is an example. When the day comes that you want to remove the package upon which it depends, aptitude would suggest that you remove this dependency because it's no longer needed. 

Happy Trails,

Loye Young
Isaac & Young Computer Company
Laredo, Texas
[http://www.iycc.net](http://www.iycc.net)

---

### Post by esmerine on 2008-01-30
> **loyeyoung said:**
> @ esmerine



Suggestion: apt-get is deprecated upstream. Use aptitude instead of apt-get, which will by default install "Recommended" dependencies. Recommended dependencies are packages that are not strictly required for the subject package to be useful, but that enable functionality that would normally be expected (I'm paraphrasing the definition because I'm too lazy to look it up). 

As an added bonus, aptitude is much more sophisticated in its handling of dependencies when you want to remove packages. Your case is an example. When the day comes that you want to remove the package upon which it depends, aptitude would suggest that you remove this dependency because it's no longer needed. 

Happy Trails,

Loye Young
Isaac & Young Computer Company
Laredo, Texas
[http://www.iycc.net](http://www.iycc.net)

Great, I'll have it in mind. :)

---

### Post by shak541 on 2008-03-23
thank you very much esmerine
you have just made my day.
today i wanted to print a label on a cd... (full picture) but i was getting that error and your fix worked and saved me. :D thank you :D

---

### Post by SirThom on 2008-03-23
> **reiki said:**
> Lightscribe burns are indexed from the media, not the drive. If you look at the innermost ring of the media... right next to the center hole... you'll see marks. The Lightscribe media is indexed on those marks. This is what makes it possible for you to burn a lightscribe image TWICE (or more) even if you remove the media and put it back in.

I'm going to jump in and say that I discovered this feature on accident when a cover I was burning was interrupted part way through and I decided to give it another go.  Now If I want a really nice looking label I run it through multiple times.  Running it through twice can make it look blotchy and uneven, but 3 or 4 times and it looks nice and dark.

---

### Post by SirThom on 2008-03-23
> **reiki said:**
> OK!  Using Inkscape I've made a template with instructions so that you can pull in a graphic, put text on a circular path, etc. All that neat stuff. It's a SIMPLE template. you can probably BREAK it so make a second copy to keep as a fresh one. It just uses layers and has some guides on it for placement and instructions for putting text on a path and ... well you'll see. 

I won't know if this is helpful unless people actually TRY it so feel free.. and let me know how this works out for you.

Not sure which attachment will work but here goes... they're the same thing but one is compressed for transport...

Thanks a billion.  I've been meaning to make one like that for ages (well, I got ubuntu working in this last week so not AGES).

---

### Post by imnotatfault on 2008-05-25
so i'm not sure if this is even monitored by those who can help anymore and sorry for the resurrection, but i have searched everywhere and can't find a solution.

I am running Ubuntu Hardy Heron and have an LG H55LK Lightscribe drive. I have installed the .deb system software from Lightscribe.com and have attempted to create a disc and failed with both Lacie's and lightscribe.com's label software.

After taking a few minutes to time out at 0%, I receive the following error message: "a communication error has occurred with the lightscribe drive. please restart your pc and try the label again."

I have restarted, uninstalled/reinstalled, nothing. Also, I am able to burn discs, if that has any effect.

EDIT: By first inserting the disk data side and receiving a wrong side error, I can then flip it to the lightscribe side and click try again and it will work.

Seems like a faulty drive.

---

### Post by slick1a on 2008-05-30
Afriend of mine bought himself a sata dvd re-writer with lightscribe, after realising he had IDE he graciously gave the drive to me.

I already had one but never used it .

So... having goten a few lightscribe disks , trawling through umpteen forums and looked at : (which may or may not be handy for some peeps)

[http://www.lightscribe.co.uk/software.htm](http://www.lightscribe.co.uk/software.htm)

[http://www.lightscribe.com/products/software.aspx](http://www.lightscribe.com/products/software.aspx)

[http://www.lightscribe.com/downloadSection/linux/index.aspx?id=815](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=815)

[http://www.lightscribe.com/ideas/labelgallery.aspx?id=219](http://www.lightscribe.com/ideas/labelgallery.aspx?id=219)

I finally installed the software. On trying Apps>sound video - I found nothing. 

So... I installed this manually as ubuntu is not yet supported by lightscribe to the best of my knowledge (someone please let me know otherwise).

Again like many of hte posts previously I too have to use windows for a number of small things like say lightscribe.

In short like the (i belive) majority of us who would love to be soul users of which ever linux distro we use...many of us STILL have to use use windows - *pains me to say windows so often*

So... what am I saying ?????

How does it work ? from installation of the software to burning your first image/disk.

A timely response would be appriciated < even though my spelling is terrible.

---

### Post by reiki on 2008-06-02
We speak typo fluently!

It appears you may have the labeling software but not the System Software. From Lightscribe.com please make sure you have both the System Software and also Lightscribe Simple Labeler. 

When you are sure you have the system software and the labeler installed, navigate to your /opt directory. You should see plainly where to find the lightscribe applications. Once you have that location you can craete a launcher either in the menu or on your desktop for launching the lightscribe labeler.

---

### Post by tk03759 on 2008-06-03
> **slick1a said:**
> 

How does it work ? from installation of the software to burning your first image/disk.

I got mine working yesterday and then I reinstalled, so as I install it, I'll mark down the steps here for you. Hopefully this works for you.

1) Download the lightscribe system software from [lightscribe.com]("http://lightscribe.com/downloadSection/linux/index.aspx?id=814")

2) Double click the .deb file and install the software. If you're on an amd64 system, put the deb in your /home/user/ folder, and run the command: "dpkg -i --force-architecture (filename).deb" replacing "(filename)" with the name. This will install the lss.

3) Download LaCie (which is a more fully featured and supported labeler for lightscribe than the official one from hp) from [uploads.mitechie.com/lightscribe]("http://uploads.mitechie.com/lightscribe/") to your /home/user/ folder.

4) Install LaCie by double clicking the .deb file. If you're on amd64, go to the terminal and do "dpkg -i --force-architecture (filename).deb" replacing "(filename) with the name. This will install 4L.

5) To create the menu item, right click your menu and click "Edit Menus." Click the group on the left you'd like to place the menu item in (ie Accessories or Sound and Video). Then click "New Item" on the left. The Launcher properties should read Type: "Application",Title: "4L LightSribe Labeler", Command: "gksudo 4L-gui" and you can select whatever icon or description you want.

Now you should be able to use that launcher to open the program.


Edit:

Also, if you want to try installing the Lightscribe Simple Labeler from HP instead of 4L, replace steps 3 and 4 with downloading the simple labeler and installing it, and then change the menu properties to Name: "LightScribe Simple Labeler",Command: "gksudo /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler"

---

### Post by slick1a on 2008-06-03
quite right i was missing said download .

all is now well.

I successfully scribed my first cd yesturday on my spare try before you buy box - I have now installed everything on my number one box and already reaping the rewards.

many thank for the advice peeps.

sufice to say lightscribe is compatible with gutsy / ubuntu...with a little tweaking and no WINDOWS of any nature involved.

slick1a rests easy.

---

### Post by bunnyhugh on 2008-06-03
> **tk03759 said:**
> I got mine working yesterday and then I reinstalled, so as I install it, I'll mark down the steps here for you. Hopefully this works for you.

1) Download the lightscribe system software from [lightscribe.com]("http://lightscribe.com/downloadSection/linux/index.aspx?id=814")

2) Double click the .deb file and install the software. If you're on an amd64 system, put the deb in your /home/user/ folder, and run the command: "dpkg -i --force-architecture (filename).deb" replacing "(filename)" with the name. This will install the lss.

3) Download LaCie (which is a more fully featured and supported labeler for lightscribe than the official one from hp) from [uploads.mitechie.com/lightscribe]("http://uploads.mitechie.com/lightscribe/") to your /home/user/ folder.

4) Install LaCie by double clicking the .deb file. If you're on amd64, go to the terminal and do "dpkg -i --force-architecture (filename).deb" replacing "(filename) with the name. This will install 4L.

5) To create the menu item, right click your menu and click "Edit Menus." Click the group on the left you'd like to place the menu item in (ie Accessories or Sound and Video). Then click "New Item" on the left. The Launcher properties should read Type: "Application",Title: "4L LightSribe Labeler", Command: "gksudo 4L-gui" and you can select whatever icon or description you want.

Now you should be able to use that launcher to open the program.


Edit:

Also, if you want to try installing the Lightscribe Simple Labeler from HP instead of 4L, replace steps 3 and 4 with downloading the simple labeler and installing it, and then change the menu properties to Name: "LightScribe Simple Labeler",Command: "gksudo /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler"

Thanks Bro, followed this howto and worked fine for me

---

### Post by VitalBodies on 2008-07-13
Greetings, I was in the middle of writing an article for my blog when I happened onto this thread. 

What are the ramifications of forcing architecture? 
And if the install fails how do you uninstall if you do force architecture? 

Seems like the SYSTEM software is fairly easy to get going: 
```
dpkg -s lightscribe
Package: lightscribe
Status: install ok installed
Maintainer: Hewlett-Packard Company
Architecture: i386
Version: 1.14.17.1
Description: LightScribe System Software
 Copyright: 2005 by Hewlett-Packard Company, All Rights Reserved.
 LightScribe System Software
```

A search for lightscribe in the Synaptic Package Manager says that nothing is found? 


The Lacie labeler or the Simple labeler seems to be a bit more challenging. 
In my initial attempt everything seemed to load ok but when I try to start either Labeler nothing seems to happen after I enter my password. 
I am not sure what to look for in the system monitor but 4L-gui, lightscribe, etc did not show up.

---

### Post by WestCoastSuccess on 2008-07-14
If you're on a 64 bit system, you MUST force architecture - download the software from the Lightscribe site, then:

#sudo dpkg --force-architecture -i lightscribe-1.12.37.1-linux-2.6-intel.deb

Then (and this is critical: YOU MUST INSTALL THE ABOVE PACKAGE FIRST, THEN THE PACKAGE BELOW. IF YOU'VE DONE IT THE OTHER WAY AROUND, IT WON'T WORK AND YOU'LL HAVE TO START OVER BY DELETING THE INSTALLATION):

#sudo dpkg --force-architecture -i 4l_1.0-r6_i386.deb

Then, to run it:

#sudo 4L-gui

If you're on a 32 bit system, same steps but omit the "--force-architecture".

Cheers and good luck - post here if you run into problems...

---

### Post by VitalBodies on 2008-07-14
Thank you so much. 
I think I did that. 
But in the case I did not...
How do you uninstall? 

sudo apt-get remove package lightscribeApplications-1.10.19.1-linux-2.6-intel.deb
And...
sudo apt-get remove package 4L-1.0-r6.i586.rpm



Also, what do you see in the Synaptic Package Manager in a system that Lightscribe works?

---

### Post by VitalBodies on 2008-07-14
**I did this:** 
sudo dpkg -i --force-architecture lightscribe-1.14.17.1-linux-2.6-intel.deb
**Then this:** 
sudo dpkg -i --force-architecture 4L-1.0-r6.i586.rpm
**I also then tried this (simple):** 
sudo dpkg -i --force-architecture lightscribeApplications-1.10.19.1-linux-2.6-intel.deb

I did reboot a few times also... 

**Although I did this:**
gksudo 4L-gui
**Instead of this:**
sudo 4L-gui
**But this:**
sudo 4L-gui
is not making anything happen either - at least at this point.

I am on 64-bit Ubuntu Hardy Heron - happily...

---

### Post by WestCoastSuccess on 2008-07-14
You can get the deb files here - just copy one at a time and paste into the address bar of your browser and hit "enter", then save the file:

[SIZE=3]download.lightscribe.com/ls/lightscribe-1.12.37.1-linux-2.6-intel.deb

[http://uploads.mitechie.com/lightscribe/4l_1.0-r6_i386.deb](http://uploads.mitechie.com/lightscribe/4l_1.0-r6_i386.deb)[/SIZE]

To uninstall:

```
dpkg --purge lightscribe-1.12.37.1-linux-2.6-intel.deb
``````
dpkg --purge 4l_1.0-r6_i386.deb

```You can type "man" before most commands to access the manual, which tells you more about the command and explains options. In this case, if you're curious, type:

```
man dpkg
```Neither of the programs appear in synaptic in my system.

Hope this helps...

---

### Post by WestCoastSuccess on 2008-07-14
I notice you used "586" instead of "386" - try "386" instead.

If you're used to windoze you're probably in the habit of rebooting; in linux it's a relatively rare thing to have to do...

---

### Post by VitalBodies on 2008-07-14
I made the mistake of reading the Ubuntu manual on the commands I suggested. : )
sudo apt-get remove package lightscribeApplications-1.10.19.1-linux-2.6-intel.deb
And...
sudo apt-get remove package 4L-1.0-r6.i586.rpm
Did not work either...

Here is what I got back on purge:
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

What might be different about my install attempt is I tried to use files from Lacie and Lightscribe rather than [http://uploads.mitechie.com](http://uploads.mitechie.com)
 	
It is interesting that these (forced) programs are lurking around with out being seem by the package manager.

---

### Post by VitalBodies on 2008-07-14
Wow, 
sudo /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler
Started the program if used in the terminal but not in the menu.
So it is clear at this point that the simple program loaded. 

I think it was super cow powers that did the trick...

For some reason did not happen before even though I copied and pasted the command in the terminal and the menu. 

Oddly...

sudo 4L-gui
sudo: 4L-gui: command not found

The other labeler only works from this site on 64-bit (at least for me) 
[http://uploads.mitechie.com/lightscribe/4l_1.0-r6_i386.deb](http://uploads.mitechie.com/lightscribe/4l_1.0-r6_i386.deb)

sudo dpkg --force-architecture -i 4l_1.0-r6_i386.deb

So this now works:
sudo 4L-gui

Still, each menu command does not launch either program???

Again thank you for your help...

Also with the Lacie program burning a disk the process does not show up in the System Monitor. 
Burning now : )

---

### Post by VitalBodies on 2008-07-14
Without any changes other than shutting the system down for the night and restarting the menus now work? 
As they say, "how weird is that?" 
VitalBodies burned a disk and it came out light (low contrast) so burned the same disk again to increase the contrast. Looks great. The original image was low contrast.

---

### Post by WestCoastSuccess on 2008-07-14
Glad to hear you got it working!

I almost always burn discs twice on high contrast setting for better results.

As an aside, you don't need "--force-architecture" when purging, just the name of the package.

I created a launcher on my top panel to launch mine:

Right click on your panel and select "Custom Application Launcher".

In the "Type" drop down, select "Application in Terminal".

In the "Name" box, call it whatever you like.

In the "Command" box, I have "/path/to/directory/lightscribe.command" - replace "/path/to/directory" with, not surprisingly, the path to the directory where you're going to create "lightscribe.command".

Go to "/path/to/directory" that you selected above (ie "cd /path/to/directory"), then type:

```
gedit lightscribe.command
``` A text editor with appear. Put this in it:

```
cd /emul/ia32-linux/usr/bin
sudo ./4L-gui

```Then hit "Ctrl" + "x" and save the file.

When you click on the launcher it should now pop up a terminal asking for your password and then run lightscribe.

I did this a very long time ago and there's probably more elegant solutions, but I recall trying all sorts of things to get it to work and this one works for me. I also copied the lightscribe logo and use it as the icon for the launcher.

Also, I found it useful to have a button on my panel to open and close the cd drawer. The Command is:

```
eject -T
```That will either open or close the drawer. That doesn't work with all drives, so you may need 2 launchers:

```
eject -r
```opens the drawer and 
```

eject -t
```closes the drawer.

---

### Post by VitalBodies on 2008-07-14
I created a new template in GIMP and Inkscape for LightScribe and am about try to new higher contrast burn. I finished the blog article with information I pulled together from number of places including your help and the the other help offered in this forum thread. It is interesting how simple and challenging getting Lightscribe going is. I would like to credit you (if you would like to be credited) on the blog article for your help. 
If so, by what name site or username?

I have been trying to support the Ubuntu community by blogging some help where I needed help. 

I credited you on the blog but can remove the credit or change what is written. Thanks again...

---

### Post by WestCoastSuccess on 2008-07-14
That's funny - I made a template with GIMP also a long time ago but forgot all about it until you mentioned it!

It wouldn't be too hard, I imagine, to make a short script that does the whole process for the user. When I get time I'll put one together and post it here (but may be a while - pretty swamped these days).

No need for any credit - it's a community effort, and any knowledge I've come by has been at the kind help of other users. Just glad you got it working!

---

### Post by VitalBodies on 2008-07-14
> **WestCoastSuccess said:**
> That's funny - I made a template with GIMP also a long time ago but forgot all about it until you mentioned it!

It wouldn't be too hard, I imagine, to make a short script that does the whole process for the user. When I get time I'll put one together and post it here (but may be a while - pretty swamped these days).

No need for any credit - it's a community effort, and any knowledge I've come by has been at the kind help of other users. Just glad you got it working!

A script would be nice and fun to see. The learning curve is getting smaller for people shifting to open source software which is great and definitely a community effort! That is the fun part : ) 

Glad you found your template. I removed the credit at your request. I would like to try the "panel trick" you wrote about also.

---

