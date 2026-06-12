---
title: "Special notebook keys: no output in either xev or dmesg"
date: 2009-03-22
forum: Hardware
---

### Post by Irfy on 2009-03-22
Many of the special keys on my Asus N50Vn notebook do not work (fn+ combinations and extra buttons) - but some of them do, so there should be hope.

[LIST]
[*]**xev gives no output when using those keys**
[*]**dmesg gives no output when using those keys**
[/LIST]

Had xev responded, I'd be able to assign the key out of the box and had dmesg responded, I'd know I need to play with freedesktop as explained [here]("http://people.freedesktop.org/~hughsient/quirk/quirk-keymap-try.html") - but now my hands are kind of tied.

Any ideas?

I'm running Ubuntu 8.10 x86_64 with kernel 2.6.27-11-generic.

To get an idea of what works and what not, I attached a photo of the keyboard: **x** means no output in either xev or dmesg and **o** means it works. Note: The external playback and misc buttons appear to be only a set of 4 hardware (touch-kind-of) buttons, whose function is modified by a switch near them, marked with **s**.

-- Irfy

---

### Post by Irfy on 2009-03-25
bump?

---

### Post by Mark Phelps on 2009-03-26
Don't want to discourage you, but I recently upgraded my Tablet PC (Fujitsu T4020) to Intrepid and xev does not show anything for the bezel keys anymore.  I restored back to my Hardy install and xev works just fine!

So, I suspect something is "broken" in Intrepid regarding xev seeing special keys.

---

### Post by Irfy on 2009-03-26
Did you have any output in dmesg when pressing your secial notebook keys?

-- Irfy

---

### Post by Favux on 2009-03-26
Hi Irfy and Mark,

I've been looking into similar issues.  I appologize for the info dump I'm about to perform.

First from [https://wiki.ubuntu.com/IntrepidReleaseNotes#X.Org%20evdev%20xmodmap%20incompatibility]("https://wiki.ubuntu.com/IntrepidReleaseNotes#X.Org%20evdev%20xmodmap%20incompatibility"):
> X.Org evdev xmodmap incompatibility
The X keycodes generated with the new evdev input driver in X.Org 1.5 are not compatible with those generated in Ubuntu 8.04 LTS and before. If you have configured keybindings for your user with a ~/.Xmodmap file, you will need to convert or disable it by hand on upgrade. 
Then from Bryce Harrington at [http://www2.bryceharrington.org:8080/drupal/node/63]("http://www2.bryceharrington.org:8080/drupal/node/63"):
> Non-functioning hotkeys - A large chunk of time this month went into investigating hotkey issues, particularly around the sleep/battery keys. That involved into digging through 'acpi-support', which I'm wondering if we need to just drop and go with straight HAL/pmutils. There are a ton of outstanding patches from Debian that we don't have, and even with them I think it may redundant. It's too late in Intrepid to do much more than duct tape, but for Jaunty this is going to need a lot of focus.
And an associated bug with link to another bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/269619]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/269619").  The bug it links to is [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267682]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267682") where Timo Aaltonen actually presents a .fdi file to prevent evdev from mistakenly grabbing things and making the battery key work.

Now this bug report [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/278839]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/278839") talks about stopping hotkey-setup and using showkey to extract some info.  It also mentions gnome-settings-daemon and how to extract info from it.

> X can only handly 256 distinct keycodes due to a protocol limitation, and due to evdev the keycodes are now standardized to match the Linux input layer - with no keycode below 256 that could reasonably be substituted for KEY_ZOOM. As a workaround, you can add your own fdi file to /etc/hal/fdi/information that maps this key to a different keycode (see /usr/share/hal/fdi/information/10freedesktop/30-keymap-module-thinkpad-acpi.fdi for an example of how this is currently done).
Is from [http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_X61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_X61")

Alright, I hope there is something useful in there for you.

Good luck!

---

### Post by Mark Phelps on 2009-03-27
Thanks for the info. At least I now know it's not specifically my machine.

The acpi-support news is not good, at least, not for my machine.  I read an extensive post about configuring an IBM thinkpad using acpi-support, so I started digging around in my directories -- and all the the files were empty!  I looked in the directory where there are acpi files by PC brand and model, and there's nothing for my brand or model machine.

So, if they've dropped xev in favor of HAL and/or acpi-support, for my machine, that means no upgrading to the new versions!

And to think, I was so elated when I was able to get everything to work under Hardy and finally quit using Vista!!

---

### Post by Mark Phelps on 2009-03-27
Favux:

Thanks again for your reply.  I did some reading about evdev and, from what I read, you still need to use xev to get the keycodes.  The article said that if xev generated no code in response to your keypress, then either the xorg.conf or the .Xmodmap files are set up wrong -- and at least for Hardy, I know they are not.  All I did in Intrepid was remove the comments that were inserted for HAL in the xorg.conf.  I didn't make any changes to .Xmodmap.

If you have any more insight into this problem, could you please reply via my other thread: 

[http://ubuntuforums.org/showthread.php?t=1107026]("http://ubuntuforums.org/showthread.php?t=1107026")

Thanks

---

### Post by Irfy on 2009-04-02
Well I played around myself and managed to get every single key work.

I also made a little guide on how to do it [at the ubuntu wiki]("https://help.ubuntu.com/community/LaptopSpecialKeys"). Tell me what you think about it.

---

### Post by Favux on 2009-04-02
Hi Irfy,

I think it is a great wiki.  Nice job!

---

### Post by Irfy on 2009-04-02
Thanks. Ideally, you'd try out the instructions and report your problems, comments, suggestions etc. under the page's [discussion page]("https://help.ubuntu.com/community/LaptopSpecialKeys/PageDiscussion") - that's the best way to improve the guide and help others :)

---

### Post by Favux on 2009-04-02
Hi Irfy,

I don't think I mentioned on this thread before that I can't pick up anything on acpi_listen.  But we think we found out what is suppose to pick up the two "missing" bezel keys and swivel hinge.  It is a kernel module called hp-wmi.  So we may be making progress too.

So I guess I did try out the instructions. :)

---

### Post by Irfy on 2009-04-02
Wow, that seems to be out of my range. From what I figure, any key should either
[list]
[*]produce something with xev,
[*]produce something with acpi_listen,
[*]produce something in dmesg, or
[*]it could hopelessly try to invoke some key event that is beyond what X can see (>255).

Now the first two you obviously tried. Have you seen any dmesg messages saying that you should use setkeycodes to set unmapped keyboard keys? Running```
dmesg | grep -i setkeycodes
```should do the trick.

Have you checked out the last option? Is the number shown by running```
sudo dumpkeycodes | awk '{print $2}' | sort -g | tail -n1
``` bigger than 255?

If both answers are no, I will be very curious :-), but rather unhelpful, since I don't have the machine to experiment :-(

---

### Post by Favux on 2009-04-03
Hi Irfy,

> Have you seen any dmesg messages saying that you should use setkeycodes to set unmapped keyboard keys?
No and running
```
dmesg | grep -i setkeycodes
```
returns nothing.

And with
```
sudo dumpkeycodes | awk '{print $2}' | sort -g | tail -n1
```
I get 255.  But interestingly when I looked in "/var/run/hotkey-setup" a while ago there is a keycode 465 paired to e001. The next two highest are e008 387 and e00e 389.  And the next highest is 255 as far as I can tell.  This naturally made me wonder.

---

### Post by Irfy on 2009-04-03
I had a quick look at kernel's input.h and see that the three keys you are talking about (465, 387 and 389) are these (in hex):```
#define KEY_FN_ESC		0x1d1
#define KEY_PLAYER		0x183
#define KEY_DVD			0x185	/* Media Select DVD */
```Then I tried```
egrep '1d1|465|183|387|185|389' `locate hotkey`
```but found nothing meaningful. It seems to me that /var/run/hotkey-setup is generated from other hotkey files and that some of them should define your >255 keys. Perhaps you should try running this egrep command to see which file actually defines your hotkeys.

Perhaps you should check what the current assignment is for those scancodes```
sudo dumpkeycodes | egrep 'e001|e008|e00e'
```

In any case, I'd suggest assigning those scancodes (e001, e008 and e00e) manually using setkeycodes to some <255 keys. You can as well make totally random assignments, just to see if it produces anything in xev when you press the bezel keys that don't work. I'd go with something like```
. /usr/share/acpi-support/key-constants
setkeycodes e001 $KEY_A
setkeycodes e008 $KEY_B
setkeycodes e00e $KEY_C
``` and these three keyboard keys should produce the characters a, b and c respectively when you press them.

I'd even go as far as to assign all non-assigned scancodes to some well-known key to rule out your bezel keys being not mapped or wrongly mapped. Here's some ad-hoc action on that:```
. /usr/share/acpi-support/key-constants
export KEY_A
sudo dumpkeycodes | egrep ' 0' | awk '{ cmd = sprintf("sudo setkeycodes %s %s", $1, ENVIRON["KEY_A"]); system(cmd) }'
sudo dumpkeycodes | egrep ' 0'
```The last command should give no output, and all the originally not assigned scancodes should produce an "a" if they are pressed on the keyboard. So try out your bezel keys now.

---

### Post by Favux on 2009-04-03
Hi again Irfy,

I appreciate your help.
```
sudo dumpkeycodes | egrep 'e001|e008|e00e'
```
yields
```
e001 148
e008 193
e00e 226
```
So they are already remapped?  I ran
```
sudo dumpkeycodes | egrep ' 0'
```
before the other commands and it gave a fairly long output of paired numbers (hex numbers each paired with a zero).  Then I ran the second set of commands and ran it again and this time no output.  I tried the two lower bezel keys and the swivel hinge (which triggers a rotation event in Windows) but got nothing.  When I tried xev it spewed some meaningless output but no reaction to the bezel keys or swivel hinge. 

The other two bezel keys still work.  DVD brings up Rythmbox and the "Q" key (which I bound to rotation) still rotates the screen.

---

### Post by Irfy on 2009-04-04
> **Favux said:**
> ```
sudo dumpkeycodes | egrep 'e001|e008|e00e'
```
yields
```
e001 148
e008 193
e00e 226
```
So they are already remapped?Yeah, and those three keycodes are in the xev visible range, so that is not the problem, definitely.

The rest just made sure the keys didn't produce any unmapped keyboard events. And since you already said acpi_listen didn't produce anything either, I'm really out of ideas :-(

It appears that WMI is yet another interface for communicating "things" from the hardware to the software, and that you'll have to stick to hp-wmi and perhaps recompile the newer kernels, try them out, hoping for the best...

---

### Post by Favux on 2009-04-04
Hi Irfy,

Thanks for trying.  I think you're probably right.  At least we now know who the maintainer on hp-wmi is.  Maybe some pleading?

---

