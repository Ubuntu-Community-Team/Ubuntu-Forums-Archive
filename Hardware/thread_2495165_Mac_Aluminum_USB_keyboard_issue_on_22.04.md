---
title: "Mac Aluminum USB keyboard issue on 22.04"
date: 2024-02-09
forum: Hardware
---

### Post by jt4u on 2024-02-09
Hello, there has been a similar threads before, but I tried the solutions and failed to fix the problem.

I'm using ubuntu 22.04 on an iMac 2013 and everything else works fine.

Basically, I have a couple of keys that are not responding as they should. The <> and #@ keys are sort of switched! 

The keyboard has a standard French Mac kayout. I have a couple of keyboards like this, one USB and the other bluetooth featuring the exact same layouts.

When I boot MacOS it is fine, but when I boot ubuntu The <> key outputs @# and vice versa. That's rather annoying obviously as those keys are used quite a lot...

I'm sure there are ways to customise the layout and/or create an alternative Keyboard type that is working. 

Most of the threads I read were rather old, often refering to X11, some saying that issue had been fixed in a later ubuntu version. 

I found some references to input-remapper and I tried version 1.4 but perhaps I didn't get how it is supposed to work, but it changed nothing at all. I pushed my luck to try input-remapper 2.0 but it failed to install properly and didn't work either.

Is there a solution? There must be a generic way to reasign keys. 

Thanks for your help.

---

### Post by TheFu on 2024-02-10
If you use X11, you can manually setup the keymap for your needs.  [https://www.x.org/releases/X11R7.6/doc/xorg-docs/input/XKB-Config.html](https://www.x.org/releases/X11R7.6/doc/xorg-docs/input/XKB-Config.html)
I don't know how Wayland supports this or if they do at all. By this stage, I'd expect Wayland to have a great answer.  A quick google says that Wayland uses XKB too.

A 2023 answer says this:
> If you want to remap your keyboard keys or mouse buttons to certain keys, use "**Input Remapper**" by sezanzeb. It's VERY simple, it has a GUI, and it just WORKS. I just have set a certain shortcut to simulate a keyboard key, works well. [https://github.com/sezanzeb/input-remapper](https://github.com/sezanzeb/input-remapper)

Or just press the _delete_ key to get started.  Ok, that's a joke. Mac's don't have a delete key.  I had the same issue on a chromebook. Very, very, frustrating.

---

### Post by jt4u on 2024-02-10
How stupid of me to try and use a keyboard that looks good and should work like any other 'listed' keyboard. 

Well, I have seen this input-remapper link, but there are different versions, the latest not installing properly on 22.04 and I can't get it to work. It is so 'Simple' to use that it confuses me! 

I must be quite thick in the head...  But thanks for trying to help me.

---

### Post by coffeecat on 2024-02-10
When I look in Settings -> Keyboard (in 22.04) it lists "French (Macintosh)" as one of the (very many) listed sources. That is, a standard layout. I wouldn't think that remapping should be at all necessary. Have you tried that setting? I'm guessing that you have, but you don't say so explicitly.

---

### Post by jt4u on 2024-02-11
Yep, you're right, I didn't explicitly say it, but it is "Français (Macintoch)". 

I found an article mentionning [COLOR=#0C0D0E][FONT=ui-monospace]/usr/share/X11/xkb/keycodes/macintosh[/FONT][/COLOR]

And tried applying their solution, but it doesn't look like it works. 

When I run [COLOR=#0C0D0E][FONT=ui-monospace]setxkbmap -query -v 10[/FONT][/COLOR]

I get this:

> Setting verbose level to 10locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     us
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc+us+inet(evdev)
geometry:   pc(pc105)
rules:      evdev
model:      pc105
layout:     us


And it leads me to think it's not relevant here, is it?

Everything else on the keyboard matches perfectly!

---

### Post by TheFu on 2024-02-11
> **jt4u said:**
> How stupid of me to try and use a keyboard that looks good and should work like any other 'listed' keyboard. 
It was a joke. People are free to like any keyboard that want. 100% personal choice. Whatever works for you.

> **jt4u said:**
> 
Well, I have seen this input-remapper link, but there are different versions, the latest not installing properly on 22.04 and I can't get it to work. It is so 'Simple' to use that it confuses me! 

I must be quite thick in the head...  But thanks for trying to help me.
Well, in 22.04, input-remapper is in the "Universe" repo from Canonical, so if you need to enable that, do so and run 
```
sudo apt update
sudo apt install input-remapper
```
The instructions in the link seem to gloss over that easy method, which is unfortunate.  I didn't write them. Looks like a developer did. Developers aren't known of creating good documentation or how-to guides.  They get fixated on what they think is most important and often forget that 90+% of the world doesn't think like they do.

---

### Post by jt4u on 2024-02-11
> **TheFu said:**
> It was a joke. People are free to like any keyboard that want. 100% personal choice. Whatever works for you.

Well, in 22.04, input-remapper is in the "Universe" repo from Canonical, so if you need to enable that, do so and run 
```
sudo apt update
sudo apt install input-remapper
```
The instructions in the link seem to gloss over that easy method, which is unfortunate.  I didn't write them. Looks like a developer did. Developers aren't known of creating good documentation or how-to guides.  They get fixated on what they think is most important and often forget that 90+% of the world doesn't think like they do.

I re-installed input-remapper (1.4 as in the universe repository for 22.04) but it still doesn't make sense to me. And the fact the developer has completely changed the design apparently for 2.0 is an indication that it wasn't clear...

Anyway, this must be a known issue. I've seen several references to this over the years. 

I'm now trying to boot up my old McBook Air from 2011 and see if it shows the same issue. The key arrangement is basically the same, at least for those @#<> keys . 

So, it looks like 23.10 has it right! That was the only usb key I had handy.

---

### Post by jt4u on 2024-02-11
Now from the Macbook Air, when I run: 

> setxkbmap -query -v 10
Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     fr,us
variant:    mac,
Trying to build keymap using the following components:
keycodes:   evdev+aliases(azerty)
types:      complete
compat:     complete
symbols:    pc+fr(mac)+us:2+inet(evdev)
geometry:   pc(pc105)
rules:      evdev
model:      pc105
layout:     fr,us
variant:    mac,



So it looks somewhat different, as it refers to **variant: mac,** and I don't have that on the iMac!

I don't know how to fix this!

---

### Post by jt4u on 2024-02-11
But there may be a good reason for this:

> # System Details Report
---

## Report details
- **Date generated:**                              2024-02-11 17:47:34

## Hardware Information:
- **Hardware Model:**                              (null)
- **Memory:**                                      32.0 GiB
- **Processor:**                                   Intel® Core&#8482; i7-4771 × 8
- **Graphics:**                                    NVE4
- **Disk Capacity:**                               1.1 TB

## Software Information:
- **Firmware Version:**                            433.140.2.0.0
- **OS Name:**                                     Ubuntu 23.10
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               45.0
- **Windowing System:**                            X11
- **Kernel Version:**                              Linux 6.5.0-9-generic



The windowing system reported when booting on a USB key to try ubuntu is **X11**

The above report is from my iMac and when booting live it's fine! @#<> are where they are supposed to be. So looks like it is a difference between Wayland and X11 as I suspect from the start.

Let me reboot normally again... And then I will try to deactivate Wayland for a confirmation...

---

### Post by jt4u on 2024-02-11
Very confusing! Restarted under X11 to check and it didn't work either. But I had implemented a 'fix' that keeps showing while I removed/reversed it:

> setxkbmap -query -v 10Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     fr,fr
variant:    mac,oss
options:    apple:badmap,numpad:mac
Trying to build keymap using the following components:
keycodes:   evdev+aliases(azerty)
types:      complete+numpad(mac)
compat:     complete
symbols:    pc+fr(mac)+fr(oss):2+inet(evdev)
geometry:   pc(pc105)
rules:      evdev
model:      pc105
layout:     fr,fr
variant:    mac,oss
options:    apple:badmap,numpad:mac




The **options: apple:badmap**should no longer exist...

---

### Post by jt4u on 2024-02-11
I'm back to Wayland and no progress at all after all this nerdy waste of time. Why is it so complicated to fix this?

---

### Post by jt4u on 2024-10-07
Initiqlly ;y proble; zqs ... OOPS! Now, I have a much bigger problem.

I did not intend to write garbage to start my post here, but it pretty much reflect what my problem is NOW.

**The keyboard layout has been reset to EN (English) and there is no way I can change it!**

No matter what I do with language or keyboard input, all I get is English and I wouldn't mind if my keyboard was a variant of Englsih but it is not. It is plain French.

The wird thing is this happenned as I restarted this iMac as I returned from vacation and I didn't do anything to cause this.

Any idea? Typing is hell with this issue. So please forgive the occasional typo! Finding the right key is far from obvious... :(

---

### Post by jt4u on 2024-10-09
Upgrading to 24.04 solved the language issue I was having, but I still have a problem with <>@# keys that are misplaced.

Thats remain a mystery and a PITA.

---

### Post by jt4u on 2024-10-10
**Update**: After some more updates and cleaning of old linux kernels, the keyboard now works fine, including #@<> key where they should be.

---

