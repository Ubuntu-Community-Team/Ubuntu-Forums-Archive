---
title: "thinking of buying a macbook"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by jtibau on 2006-12-20
hi all,

I'm thinking of buying a macbook...
I've read the threads about how to install ubuntu on it but they all focus on the idea that you should just keep OS X around. I don't think I'd want to use it much, it may be pretty but it's not free software. Most howtos also expect you'd want a triple boot with windows.
I have a couple of questions to some Mactel owners:
I've read about overheating problems... Are they bad/real?
Any hardware incompatibilities? Can you use everything?
Most important, would you recomend it? I'm considering a XPS M1210 a Toshiba U205 and the macbook... I expect apple provides better build quality and of course looks :)

Thanks for the opinions

---

### Post by dani_bcn on 2006-12-20
Hi

I've a new macbook with me. I've installed ubuntu and it's really easy. So far things that are not working are:

- Wifi (some people have it working with ndiswrapper)
   Not working with madwifi modules right now, but will be soon or later.

- fn keys
   Don't know why, but I expect it to work soon too

- Webcam
   i don't know, never tried. But it work with the old macbook version

- Bluetooth
  I don't know, will try soon when I get my bluetooh phone.

The laptop is very nice, and it gets hot but like my old acer centrino. Well It was worse with the acer because the hotest part was the touchpad.

It's a good idea to buy that laptop, it's really cool :)

---

### Post by jtibau on 2006-12-20
I currently own a Toshiba A105... Performance is quite nice, I even installed LTSP and had it serving another 4 thin clients :) however I'm disapointed by build quality. Very disapointed... Screen flexes a lot in my opinion. If you press certain spots it creacks. Keyboard isn't stiff enough, bends in the middle. I read somewhere that the U205 is somewhat alike in that aspect so I think I'll stay clear out of that one.
Did you follow any of the howtos for installing ubuntu? I've read wifi works since it's basically an atheros chip... I would really need this although as you said it should get fixed pretty soon.
I've read about Parallels Desktop too... Does it come with the Macbook or is it a separate buy?

---

### Post by mustang on 2006-12-20
> **jtibau said:**
> I currently own a Toshiba A105... Performance is quite nice, I even installed LTSP and had it serving another 4 thin clients :) however I'm disapointed by build quality. Very disapointed... Screen flexes a lot in my opinion. If you press certain spots it creacks. Keyboard isn't stiff enough, bends in the middle.

Would you mind expanding on this a little bit? I'm actually weighing either a macbook or the Toshiba A105 (which is significantly cheaper and has many more features). I tried out the A105 at the store and it did feel kind of weird. Then again, I've never owned a laptop before. 

The thing with the macbook is you get many less features. No VGA out (have to buy a $15 adapter), no S-video out (have to buy another $15 adapter), no memory card reader, less USB ports, less RAM, smaller hard drive. The only selling points of the macbook is that a)you can run OSX and b)build quality. So I'm still in the process of weighing those pros and cons.

> 
Did you follow any of the howtos for installing ubuntu? I've read wifi works since it's basically an atheros chip... I would really need this although as you said it should get fixed pretty soon.


I believe this is the defacto guide as of yet: [https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook)

> 
I've read about Parallels Desktop too... Does it come with the Macbook or is it a separate buy?

Separately--costs $50.

---

### Post by Seq on 2006-12-20
I have the "older" macbook with the 32-bit Core Duo. I'm actually really impressed with it. No real heat issues when used on a table or similar surface. If I keep it on my lap, it tends to warm up, however. Very light and easy to carry around. The "older" macbook's wireless is 802.11b/g and fully supported. 

I was playing around with feisty, and it has an updated kernel which fixes a problem with suspend in the piix-ide (or something like that) driver so suspend should work in that release. It also includes the appletouch driver so two/three finger taps and scrolling work (though there is some issues with getting this to load sometimes). There is also the modesetting intel driver for testing which removes the need for 915resolution.

As dani_bcn pointed out, there is the new macbook with the 64-bit Core 2 Duo. It is largely the same from what I can tell (Though I have not had a look at one), but has a currently unsupported 802.11b/g/n wireless card. Possibly from his/her comments as well, they may have some new keyboard as I did not have issues with the fn keys (aside from having to set it to "Shift" mode)

Update:

Also, to answer a question, you will want to keep OS X around for firmware updates through apple's updater. You could do this with an external firewire disk if you so desired.

---

### Post by jtibau on 2006-12-20
> **mustang said:**
> Would you mind expanding on this a little bit? I'm actually weighing either a macbook or the Toshiba A105 (which is significantly cheaper and has many more features). I tried out the A105 at the store and it did feel kind of weird. Then again, I've never owned a laptop before. 


This Toshiba A105 is my first laptop too. I use it for school so now I get the feeling I should've bought a smaller one. It doesn't necesarilly feel heavy to me, but compared to some friend's lappys it is kind of bulky. Hence my primary "need" to switch to a smaller one.

I'm disappointed in a couple of areas. Before I got this I thought highly of Toshiba. Now there are several issues that deeply makes me dislike them. Here's an ordered list of what pisses me most:
- Build Quality. It doesn't look bad, but once you start using it, it feels very cheap. Exert pressure anywhere and you are almost sure to hear it creak. The LCD flexes a lot more than I would like to see it do. When it is closed if you unintentionally press the top, the screen will get marks from the keyboard.
- Can't get the VGA out to work. Granted, I haven't messed around with xorg.conf enough to ensure it is not posible. Maybe it's a frequency issue but I can't figure it out. I think the same thing happened with Windows when I had it. Really pisses me of since I often give speeches about GNU/Linux and FOSS at school, I need to borrow a friend's laptop for them, and that just sucks!
- SD/xD/Memory Stick slot doesn't work... Not with edgy anyhow. I've read it's a hardware problem, it's not very generic or something.
- Fn keys don't work either. I can't lower the screen brightness which basically means that battery life is way shorter than it should. And it is a big pain to use the laptop on prolonged coding sessions at night.
- Last of all, the optical super drive makes a weird whiny noise sometimes when it plays DVDs. I think it has something to do with a hardware feature that lowers spinning speed to safe energy. The noise is very obnoxious though, it's like the disc is scraching something in the inside.

I haven't used the S-video output I think... Or maybe I've tried but I expect I got the same results as with the VGA output.
Other than that it works pretty well. I would say it is a decently good cheap system. But I expected a lot more from Toshiba, I had heard that they where more linux friendly... This little piece of work deffinitely isn't  that much :(

I think that if the chance arises soon I will buy a macbook and get rid of this one. I'm going mostly for apple's better build quality :)

---

### Post by svenand on 2006-12-22
I am running Ubuntu Linux 6.10 in a virtual machine (Parallels Desktop) on my MacBook.
Everything works fine. Wlan using Airport no problem. I have a Bluetooth keyboard and a
BlueTooth mouse attached without problems. I have written about my experiences in my blog: svenand.blogdrive.com

---

### Post by celloandy on 2006-12-22
I've got a Core 2 Duo Macbook.  Overall, it's a really nice machine, and they're very reasonably priced.  Running Linux on it is still pretty rough around the edges, though.  You've got to run a custom kernel to get some things working (scrolling or two-finger-right click on the the touchpad, for instance).  At the moment, I'm running 2.6.18.3 with the mactel patches, which works fine, but I'd like to upgrade to 2.6.19, to fix some scratchiness with the sound and get software suspend working, only, at present, ndiswrapper kernel panics 2.6.19 on the macbook, and madwifi doesn't support the new chipset, yet... these sorts of things have been typical, so far.  Most things work, and eventually everything will, I'm sure, but it'll take some time, and in the meantime, it can be a bit of a pain to make everything work.

If you get one and have any questions, feel free to PM me, as I've overcome most of the Macbook2 hurdles, I think.

Andrew

---

### Post by haiku99 on 2006-12-22
edit

---

### Post by morphet on 2007-01-15
I think you should be completely fine if it is intel-based. You might need a whole day of tweaking, and then some llittle time during the next 2 weeks, but nothing big. I have a imac G5 with the ppc processor, and I can tell you I love ubuntu, but would like to be able to tap into all the 386 support.

---

