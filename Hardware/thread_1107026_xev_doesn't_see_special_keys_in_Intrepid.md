---
title: "xev doesn't see special keys in Intrepid"
date: 2009-03-26
forum: Hardware
---

### Post by Mark Phelps on 2009-03-26
Opening a new thread because this is a specific problem with xev, special keys, and Intrepid.

Recently upgraded my Tablet PC from Hardy to Intrepid.  Noticed that the bezel keys no longer functioned.  Checked all the key-related stuff (xbindkeys, Xmodmap, etc) and all of it was the same.

Ran xev and notice that now, under Intrepid, it no longer responds AT ALL to any of the special keys -- the buttons on the tablet bezel.

There is the possibility that the keycodes have changed under Intrepid (others have found that to happen for some of their keys), but without something being seen in xev, know of no way to change the custom keymappings to use the "new" codes.

Did a restore back to Hardy (I saved off images of my Linux partitions) and immediately, the bezel keys were working again.  Opened a terminal with xev, and was able to see results for ALL the bezel keys.

So, xev in Intrepid is simply NOT seeing the bezel keys.

I checked /etc/modules in Hardy to see if I was loading a module for the keys, and there is nothing like that in there. The only modules are fuse, lp, sbp2, and i2c-i801.

Anyone have any ideas why xev would behave differently under Intrepid?

---

### Post by Favux on 2009-03-27
Hi Mark,

As I get it from the first quote it is the new evdev input driver in Xorg 1.5 that is responsible for changing the key code numbers.  That's why mine went from 205 to 201 for example.  You would seem to be right that that shouldn't stop xev from picking up the new key codes.  But it did with me.  So I think you may need to do a hotkey update similar to the Key code addendum I referred to.  I couldn't pick up xev from the two bezel keys until I did that.  I'll try to  check into that.

---

### Post by Mark Phelps on 2009-03-27
Sorry to be dense but I don't know what addendum you mean.

I started reading ALL of the things you linked but got discouraged because I had tried the thinkpad stuff before only to discover that my machine doesn't generate any of the special IBM events and it also does not appear to load any special acpi module.

But I did see something about turning off a daemon.

I've got Hardy loaded back because I need to use the machine daily.  I'll see what I can do about some testing this weekend and get back to you.

---

### Post by Favux on 2009-03-27
Hi Mark,

I know, my eyes glaze over on this stuff.  I can see what I'd need to do but it looks like hours of work traveling down one dead end after another.  We may have finally figured what controls our two dead bezel keys (2/4 never worked with Hardy or Intrepid) and swivel hinge.  It turns out there is a kernel module called hp-wmi.  MisteR2 has now gone to the Ubuntu dev.s on a bug report.  We'll see.  Anyway these are the commands I'm talking about:
```
sudo update-rc.d -f hotkey-setup remove
sudo update-rc.d  hotkey-setup start 99 1 2 3 4 5 6 .
```
As you can see it's basically a hotkey update.  It's what reactivates the TX2*'s two bezel keys that died with Intrepid.  But I don't understand it totally, esp. the start 99 stuff.  I've asked the guy who came up with them (gali98 ) if they'll work for you or if not what will.  He's pretty busy so he might not answer right away.

Hang in there.

---

### Post by Mark Phelps on 2009-03-28
Favux:

Yeah, it's a lot of stuff to absorb.  I looked into the acpi-support stuff when I was reading about the thinkpad and found that the toshiba module has lots of entries, whereas the siemens-fujitsu module has only two, one one of them is for sleep which I can confirm does NOT work.

Haven't been able to find anything much on hotkey-setup, though.

Going to be busy after all this weekend, so I many not be able to get around to imaging my tablet, reloading Ibex, and testing.

But, Ill stay in touch.

Update:  Booted the tablet PC from the latest Jaunty Beta -- and still no responses to bezel keys in xev.

I read the forum and bug posts again, killed off the processes they suggested, removed the files they suggested.  Still, no detection of bezel keys.  

As a test, to rule out the possibility that I had installed a kernel module and/or a driver in Hardy that allowed the detection of the bezel keys, I booted from a Hardy LiveCD and ran xev again.  And again, it detected the bezel keys just fine.

So, if the 8.10 and 9.04 kernels can't see the keypresses, then I don't know what to do to fix this.

---

### Post by Irfy on 2009-04-02
Cross-posting since [you asked]("http://ubuntuforums.org/showpost.php?p=6967539&postcount=7") to post in your thread too :-)

> Well I played around myself and managed to get every single key work.

I also made a little guide on how to do it [at the ubuntu wiki]("https://help.ubuntu.com/community/LaptopSpecialKeys"). Tell me what you think about it.

---

### Post by Favux on 2009-04-07
Hi Mark,

I think I've made progress on the hotkey-setup thing.  Check posts #96 and #97 here:

[http://ubuntuforums.org/showthread.php?t=996830&page=10](http://ubuntuforums.org/showthread.php?t=996830&page=10)

Let me know what you think.

---

