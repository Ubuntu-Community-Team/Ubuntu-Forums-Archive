---
title: "Should I have problems with Ubuntu on Dell XPS M1210?"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by 1002285 on 2006-10-30
I'm going to buy a new laptop and am thinking of Dell XPS M1210.
Does anybody know about possible problems with Ubuntu and this computer? re there good places to find information on this?

---

### Post by jbNet on 2006-11-04
I just bought mine, and it's really nice. I upgraded from a Dell 700m. Only problems I've noticed so far are hibernate doesn't work (but suspend does), and the brightness keys don't work.

I suspect the brightness problem is due to Ubuntu intercepting the keystrokes or some such thing, because I found a post somewhere that said they did work for somebody else.

Anyway this is a really nice machine, high recommend it.

---

### Post by 1002285 on 2006-11-05
> **jbNet said:**
> I just bought mine, and it's really nice. I upgraded from a Dell 700m. Only problems I've noticed so far are hibernate doesn't work (but suspend does), and the brightness keys don't work.

I suspect the brightness problem is due to Ubuntu intercepting the keystrokes or some such thing, because I found a post somewhere that said they did work for somebody else.

Anyway this is a really nice machine, high recommend it.

Thanks. I had already bought it anyway before the answer though :).
I haven't had time to install Ubuntu yet.

So the mediaplayer buttons should work?
What are the brightness keys?

---

### Post by jbNet on 2006-11-05
The media keys work for me. The brightness keys I'm talking about are Fn up/down, the ones that control the brightness of the LCD.

---

### Post by 1002285 on 2006-11-12
> **jbNet said:**
> The media keys work for me. The brightness keys I'm talking about are Fn up/down, the ones that control the brightness of the LCD.
The brightness keys worked for me out-of-the-box.
Media keys don't work perfectly (volume keys don't), but that does not bother me so far.

What doesn't work is the webcam. Can it be installed?

---

### Post by xiangpeng on 2006-11-14
I installed the nvidia driver from amaranth's repos and i now get a crackling sound whenever i play opengl games or run beryl.

It shouldn't be a problem for you if you are not using the geforce configuration.

---

### Post by 1002285 on 2006-11-14
> **xiangpeng said:**
> I installed the nvidia driver from amaranth's repos and i now get a crackling sound whenever i play opengl games or run beryl.

It shouldn't be a problem for you if you are not using the geforce configuration.

But I don't think I have NVidia, it's Intel's own video, I got the cheapest configuration.
Anyway, if there is a point in trying the amaranths repos - what's the line for these repos?

---

### Post by TrAvELAr on 2006-11-15
I ordered my M1210 last Friday and it arrived yesterday (4 days after ordering, it must be some kind of record for Dell).  I installed Edgy x64 on it and it ran horrible.  After switching to the x86 version, I have had no problems whatsoever.  Just about everything works and I'm quite pleased with it.  

This is the first release where I got the native resolution (1280x800) natively without having to deal with 915resolution.  I'm quite happy!

---

### Post by dimeotane on 2007-01-13
I now have Edgy 6.10 installed, but have yet to get anything else working;  the correct screen resolution, the wireless, card reader and so on.  

The Dell XPS m1210 has many different variations and configurations.  I learned the hard way that when dell puts on a 'boxing week sale'  basically there's no sale, they've only stripped the high end components to replace with less expensive.  My M1210 is different than the usual one for sale, it's missing a few hundred in better components. I figured this out 5 minutes after I entered my order when the email order confirmation lists all the components. I noticed there was no camera, no bluetooth, the incompatible and cheaper Dell wireless card.    I clicked on the link to report an incorrect order, But by the time Dell recieved and responded to that, my shipment had already arrived one week later.    Needless to say I don't think this reflects well on Dell inc.  So if you're thinging of buying a Dell on sale... buyer beware, and be very very carefull in checking to make sure that it has every component that you think it should have before you place your order.  You won't get the same unit that they sell at the regular price.  :evil: 

*IF* I manage to get *my* version of the m1210 working I'll be sure to post the how to online.

---

### Post by golem3 on 2007-01-21
Can I get an official report from someone saying 

1) That the Media Keys do work, or that they CAN work.

2) That Dell's media Direct works without issue (its runs on its own partition, right?)

3) Brightness and other Fn keys work /or not work.

---

### Post by 1002285 on 2007-01-21
> **golem3 said:**
> Can I get an official report from someone saying 

1) That the Media Keys do work, or that they CAN work.

I have mostly used only volume keys and play/pause.  The latter works always, I think.
Volume keys sometimes regulate the wrong thing, or do not regulate anything. Gnome volume control (the one you can open from top right corner of the screen) has different things like "front" and "headphone"  and they act strangely anyway, I think. For example sometimes you have to change the "front" level to get the actual volume to change and sometimes "PCM" etc. I cannot understand the logic at all. For example now the buttons change only the "headphone" level - which actually changes the volume, although there are no headphones.
Mostly the volume buttons work. Pause works even with swf stream that I'm seeing now.
> **golem3 said:**
> 
2) That Dell's media Direct works without issue (its runs on its own partition, right?)

I don't know about that and I don't know how to check. I don't even know what the media direct is.
> **golem3 said:**
> 
3) Brightness and other Fn keys work /or not work.
[/QUOTE]
Fn keys:
Brightness works, Stand by works, Hibernate works (although the hibernate itselt does not always work in Ubuntu, but the button gives the command), Print Screen works. Pause/Break in Beryl gives me a view of all windows where you can then choose which one to activate - the same thing you get moving mouse cursor quickly to top right corner. Don't know what it does without Beryl.
There's a button next to Alt Gr that gives you right click menu (in Ubuntu, I have never even known about it and have not checked what it's actually for - probably the same thing?).

What I have not got to work is the webcamera - I have tried EasyCam but it just says sth like "not compatible" (in french). I hvae not tried very much, because I don't really need it.

---

### Post by golem3 on 2007-01-28
Thanks 100228...

Now I just need to find out if MediaDirect can read from the EXT3 partition.

---

### Post by stryderjzw on 2007-02-01
> **golem3 said:**
> Thanks 100228...

Now I just need to find out if MediaDirect can read from the EXT3 partition.

My MediaDirect is broken.  GRUB messes it up.  However, I did read somewhere (I think notebookreview.com forums or sth) that someone tried to hack GRUB to make it work with MediaDirect.

However, I don't miss MediaDirect at all.  Nothing too special.  :)

My suspend/hibernate is funky.  Dunno if it was the tweaks I made on it or if Beryl did something to it, but it only works 50% of the time for me.

---

### Post by vrod74 on 2007-02-05
I have my M1210 working with 6.10 Edgy... Works Great!  I got with the NVidia Adapter, so I to manually install with the "nvidia binaryX.org drivers, which you can grab from the respiratory. After that I had to modify xorg.conf to display 24 bit and to actually enable the driver to "nvidia" manually. Other than that I installed UT2004 and it just rocks!

---

### Post by appsmanster on 2007-02-05
> **stryderjzw said:**
> My MediaDirect is broken.  GRUB messes it up.  However, I did read somewhere (I think notebookreview.com forums or sth) that someone tried to hack GRUB to make it work with MediaDirect.

However, I don't miss MediaDirect at all.  Nothing too special.  :)

My suspend/hibernate is funky.  Dunno if it was the tweaks I made on it or if Beryl did something to it, but it only works 50% of the time for me.

If you want MediaDirect to work as it did when the lap arrived you need to look a grldr. After creating a separate boot partition make sure grub is set to boot from it and not to overwrite the MBR. Add grldr and menu.lst to the c:\ directory. Add C:\grldr="Start Linux Loader (Grub)" or what ever you want it to say within the quotes, to the boot.ini. Modify menu.lst to look for the boot partition with the correct kernel. Mine was in hda7 which meant that the boot partition I entered was (hd0, 6). Now I can boot to linux, windows, and MediaDirect works with the button. MediaDirect is nice for not booting a full windows XP. Not sure if grub will boot this partition as I do not need to know this. I will tell you that grub sees this partition as embedded Windows XP.

---

### Post by dimeotane on 2007-03-08
I've actually quite enjoyed using edgy on this wonderful laptop.  

Current complaints with my configuration:
1)  brightness keys work only sometimes ie when the system is booting.
2) standby didn't work, then did after I edited the beryl configuration and then broke again with an update.
3) here's a HUGE one... the mic input is borked. you plug in a headset for VOIP and there's hiss at best- everyone I've read says it's the same.  If you manage to get the M1210 users know!
4) media direct has never worked since I first put ubuntu on after resizing partitions

---

### Post by jgcamp99 on 2007-03-08
Purchasing that model shouldn't be tainted or influenced by whether or not Ubuntu works on it. It comes with Windows XP or Vista, that said, as a package you get a quality product. Linux is a bonus for any notebook.

I just got a freebie, a Dell L400 P3 700 10 GB hdd, 256 MB PC133. Anyway, this notebook needs a special floppy/optical drive setup to install anything Windows OS that I don't have or got with this notebook. USB drives won't boot. Ubuntu provided a PXE network/internet installation. That went flawlessly. Wireless was a challenge and a Proxim Orinoco Gold PCMCIA purchase later, I got wireless working and even a Netgear MA401RA Rev D that everything on the internet tells me shouldn't work with Edgy. Well, it woks fine too. I got something to work right by working hard at it and it's paid off. This post comes from that Dell L400 and Edgy.

From this day forward, this notebook is a Linux notebook and I hope to be able to clone the hdd just in case this hdd ever dies or I upgrade it. With DSL, it's still a fine ultra portable. It's my road warrior for the light stuff.

---

### Post by jimbojones on 2007-03-09
I am currently experimenting with Ubuntu 6.1 on my 1210.
My brightness keys do NOT work when I am in my desktop, it logs me out and brings me to a login screen.  Anyone who has ones that work- did you have to disable anything to get it to stop logging you out?

---

### Post by stryderjzw on 2007-03-10
> **jimbojones said:**
> I am currently experimenting with Ubuntu 6.1 on my 1210.
My brightness keys do NOT work when I am in my desktop, it logs me out and brings me to a login screen.  Anyone who has ones that work- did you have to disable anything to get it to stop logging you out?

That's weird, I never had problems with my brightness keys.  I am using Edgy and it works right out of the box.

You mean Fn+Up and Fn+Down keys, right?

---

### Post by jimbojones on 2007-03-15
> You mean Fn+Up and Fn+Down keys, right?

Yes that is correct

---

### Post by HokkaidoHillbilly on 2007-04-01
Yeah, I get the same weird log-out problem when I press Fn+up, so just know that you're not alone.  Here's hoping this'll be fixed later on this month.

---

### Post by xboxbman on 2007-04-03
my brightness keys work just fine.  Damn I love this machine!!  Just about everything works perfect, except the rare occasion the speakers don't work for no reason,  or the webcam has very little use at the moment, just in ekiga.  Otherwise, Ubuntu works like gold

---

### Post by 1002285 on 2007-04-03
> **xboxbman said:**
> my brightness keys work just fine.  Damn I love this machine!!  Just about everything works perfect, except the rare occasion the speakers don't work for no reason,  or the webcam has very little use at the moment, just in ekiga.  Otherwise, Ubuntu works like gold

How did you get the webcam to work? I have not found a way to do it. And I cannot get the microphone working either. Otherwise, everything is fine.

---

### Post by HokkaidoHillbilly on 2007-04-15
Yeah, my built-in mic doesn't seem to wanna work for some reason either.  Supposedly, adding:

```
 options snd-hda-intel model=ref
```

in /etc/modprobe.d/alsa-base then restarting & playing w/ alsamixer will fix this issue, but I still get no love.   I really hope that these issues'll be fixed w/ the final release of Feisty, but something tells me it won't...at least for a while. :(

---

### Post by YourBabysDaddy on 2007-04-19
solution for Wireless -n cards: [http://ubuntuforums.org/showthread.php?t=342558&highlight=xps+m1210](http://ubuntuforums.org/showthread.php?t=342558&highlight=xps+m1210)

---

### Post by lcohen999 on 2007-04-28
> **1002285 said:**
> How did you get the webcam to work? I have not found a way to do it. And I cannot get the microphone working either. Otherwise, everything is fine.

for the webcam, google linux-uvc I have not tested the mic though...

---

### Post by afljafa on 2007-05-06
I gather by this thread that you guys are happy with this lappy from a hardware perspective. Thinking about grabbing one as a travel with me work machine.

Looks reasonably robust.

---

### Post by whirl on 2007-05-24
Ive been thinking about this one too.. I found ubuntu few weeks ago and now I try to avoid windows like plague but now Im thinking of buying a laptop and it seems that in generally laptops are having some problems moving in with ubuntu..

Any news how XPS M1210 works with new feisty? Or better yet please tell me what doesnt work.

o/

---

### Post by afljafa on 2007-05-26
> **whirl said:**
> Ive been thinking about this one too.. I found ubuntu few weeks ago and now I try to avoid windows like plague but now Im thinking of buying a laptop and it seems that in generally laptops are having some problems moving in with ubuntu..

Any news how XPS M1210 works with new feisty? Or better yet please tell me what doesnt work.

o/

Pretty much everything works out of the box including the webcam. Havn`t tried the modem.

This is a great laptop - robust and has a superb screen.

---

### Post by lcohen999 on 2007-05-28
I just wish suspend with the NVIDIA card worked :(

---

### Post by marcdel on 2007-05-31
Just to clarify, because I've heard different things in different threads, does the wireless card work out of the box, or do you need ndiswrapper (specifically in 7.04)? Thanks.

---

### Post by razorsmile on 2007-06-03
> **afljafa said:**
> Pretty much everything works out of the box including the webcam. Havn`t tried the modem.

This is a great laptop - robust and has a superb screen.

Just to say that this has not been my experience, though I do love the laptop.  Ubuntu is definitely less clean and efficient than Vista on this machine.  No doubt a lot of these problems I mention below are fixable and I would LOVE any suggestions as to fixing them...I'm not a complete newbie (got Ubuntu running on three machines, two of which are laptops, and have been running it for about a year, though I'm still getting used to things and haven't yet really become au fait with hardware management which seems to be the key here)

Concretely...

webcam - can't get this to work, though possibly this is due to it having to be configured in some strange way.  Camorama just says can't connect to device /dev/video0.  someone sugegsted trying linux-uvc but the project is definitely in early development stage or only for those with considerable experience...I eventually found the files but I'm very wary of downloading and trying to make/configure myself since I'm not even clear which files I would need...so in effect webcam down (which also means the mic is down)

card reader - seems not to work - again, perhaps this is a matter of me having to find the excat location of hardware, then track down the software that I need to plug this into and then find a decent gui to use it - again, in effect, card reader down

suspend seems to work if I DON'T use proprietary nvidia drivers...that seems to mean at the moment that the 3d doesn't work since I could run sauerbraten with the nvidia drivers on but no longer - in effect at the moment my 3d doesn't work

the fan also seems to be constantly running and the laptop runs at around 50 degree C
the play/pause/volume buttons at the front do work
the basic keyboard shortcuts in gnome (without beryl where they all seemed to **** up) work well it seems

main bugs really are the constant fan (knowing that fans are always a weak point in laptops makes me wary of now running Ubuntu continuously...but again, this is probably some sort of setting I can hack around with when I eventually find the info on the boards/web) the lack of webcam and mic, the lack of 3d and the card reader.

One good thing though, is that Vista has some odd F'ing network issue and so can't connect to my local network properly at the moment (2 ubuntu and one xp machine) whereas no worries on that score with Ubuntu on this laptop...

so a mixed bag for me...I'm predominantly in Vista at the moment snice it's a lot smoother and prettier (teh sidebar and the RSS update app in the minimise tray are very good and if i could strip Vista down a little I'd probably stick there but since I can't I'll no doubt eventually get the laptop working how I want with Ubuntu...we'll see...I'd like to be able to but in the end it's a matter of which allows the work and fun the most easily...)

#-o

---

### Post by stryderjzw on 2007-06-03
> **marcdel said:**
> Just to clarify, because I've heard different things in different threads, does the wireless card work out of the box, or do you need ndiswrapper (specifically in 7.04)? Thanks.

I'm on Feisty. Wireless works out of the box, but it is a "Restricted Driver".  I have no problems with using restricted drivers though.

---

### Post by marcdel on 2007-06-05
> **stryderjzw said:**
> I'm on Feisty. Wireless works out of the box, but it is a "Restricted Driver".  I have no problems with using restricted drivers though.

Any idea if the driver supports monitoring mode?

---

### Post by stryderjzw on 2007-06-05
> **marcdel said:**
> Any idea if the driver supports monitoring mode?

Sorry, I've never tried that. :(

---

### Post by marcdel on 2007-06-05
> **stryderjzw said:**
> Sorry, I've never tried that. :(

No worries, thanks for the help.

This post on the Kismet forum seems to suggest that it does support monitor and promiscuous mode. [http://www.kismetwireless.net/Forum/Equipment/Messages/1166562769.454711](http://www.kismetwireless.net/Forum/Equipment/Messages/1166562769.454711)

---

### Post by localgod11 on 2007-10-04
I have had mine for about 2 months now and everything works I dont have a webcam or Draft-n but i do have Nvidia,  and it works great I am typing through the compiz-fusion rain drops ATM. even the card reader works. I doubted the media parition after i found out there was no real battery saving in it and vista has MCE built in so no loss there. let me say I love this ubuntu on this laptop and I am a total linux newb but proficent in winders and everything has been awesome I have actually have had more trouble with vista randomly crashing me laptop so I booted to ubuntu about a week ago and havent been back since I had a little trouble getting used to linux and getting compizfusion (i like saying beryl better) but nothing a few trips to google cant fix, 


BTW if you cant get vista to play nice with your network you might wanna trying turning off IP6 since most routers dont play well with it.


ALSO if your thinking about a 1210 the are still some for sale (and for a steal) at the Dell outlet, not plugging them just a happy customer.

---

