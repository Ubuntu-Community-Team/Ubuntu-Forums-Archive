---
title: "Newbie Toshiba questions.. freezes on shutdown, and probs with toshutils"
date: 2005-02-25
forum: Hardware &amp; Laptops
---

### Post by SurreaL on 2005-02-25
Hello everyone!

As I mentioned in another thread, I'm a little new to Ubuntu but have it installed on 3 machines so far and am loving every minute of it :) (I've only had a little experience with Debian before but so far so good!) The only problem I'm running into atm is on my laptop.. which is a Toshiba Satellite 1800 (model PS181C-00WZX) I've got sound, networking, and even my wifi working.. gnome running smoth.. Everything seems ok, except for one thing. I've tried to load toshutils, installed the .deb package, but running any commands from it give the error "this computer is not supported or the kernel module is not installed."

I decided to give toshset a shot, which is similar except apparently works with an experimental ACPI driver. Turns out when I do a lsmod, it looks like that driver has already been loaded by the default Ubuntu (Hoary) install.  The module is toshiba_acpi. Toshset just says 'required kernel toshiba support not enabled'. which is why I'm wondering if I should play around with re-compiling it.. I just don't want to break any other things while doing so :/

Anyhow the reasons I wanted to do this were basically to try to fiddle around with the screen brightness (which seems a little dark), as well as to see if somehow I could make the laptop stop freezing all the time whenever I try to shutdown/reboot.

So I suppose I *could* try to re-build the kernel.. but I'm sort of concerned to do this because I know that the kernel that you can download does not natively support my Atheros chipset wifi card. (I'd need madwifi, which was conveniently installed for me somehow already) Basically since I don't know how the pre-built kernel was compiled, I don't know how to appropriately tweak it to try to fix the problems I've been having :/ (Namely the shutdown glitch) I had spent ages trying to compile the madwifi drivers myself until I found a thread on here about just doing "apt-get install linux-restricted-modules-`uname -r`", which seemed to fix everything.. so now I don't want to undo what was done.

So I guess my questions are, does anyone else have similar experiences with their Toshiba Satellite that they've overcome? Is there any way I can figure out what config was used for the kernel I'm running? and if I *do* re-compile the kernel, is there any way I can be sure that it doesn't over-write or somehow remove my currently working wifi modules? Would it be safe to just copy them over to the new kernel and assume that a depmod would do the rest for me?

I think if I feel brave enough my next step may be to try to see
 if I can install a slightly less resource-intensive window manager.. as gnome seems a bit sluggish on this p3-750 w/ only 128 megs SDRAM. Any suggestions? I'm leaning towards possibly IceWM as well as trying out Rox instead of Nautilus..

but yeah.. Thanks everyone :)

---

### Post by jMack on 2005-02-25
Interesting.

I'm just about to do my first install of Ubuntu, and I'm doing it on a brand-new laptop from Bestbuy; a Toshiba Satelite (M35X-S111) going for $500 after rebate.

That said, I've been doing some searches online to find as much support I can for this laptop-going-linux, and I've found the following sites:

[http://www.buzzard.org.uk/toshiba/](http://www.buzzard.org.uk/toshiba/)

[http://www.linux-on-laptops.com/toshiba.html](http://www.linux-on-laptops.com/toshiba.html)

[http://linux.toshiba-dme.co.jp/linux/](http://linux.toshiba-dme.co.jp/linux/)

You seem informed enough to know this, but I thought I'd give what I got.  I especially love [www.linux-on-laptops.com](www.linux-on-laptops.com), as they show personal walk-throughs with specific toshiba laptops and distros.  I found one where a user was installing Warty on a nearly-compatible laptop as mine which is great because he already ran into the few headaches and posted solutions to them!  A great timesaver.

---

### Post by lucan on 2005-02-26
hi,
i'm new to linux, and i just install ubuntu on my compaq (armada e500) laptop.
but ubuntu cannot find the network card i put in (linksys notebook adapter). it also show me the battery at 0%. best of all, when i log out, it wouldn't shut down, just hang down there. i have to remove the battery to forcely shut it down. how can i fit it? thanks.

---

### Post by mordecai on 2005-02-27
Hi,

I had the same problems with my toshiba satellite a50-110. 

To change the screen brightness and other sound options you can install the fnfxd and fnfx-client packages. It's necesary to load the toshiba_acpi module ("sudo modprobe toshiba_acpi", or add a new line with "toshiba_acpi" in the /etc/modules to load it at startup).

I still have the reboot problem, my laptop freezes when I try to reboot it. It's seems a acpi problem. You can try to disable the acpi, but I really want to use the acpi features.
Any other idea for the reboot problem?

---

### Post by awahl on 2005-02-27
Hi Surreal...

  I am running Ubuntu on my Tosh Satellite S5205, P4 2.0 w/512mb, etc.  Everything installed fine, even sound worked right from the get-go. No probs with my wifi, etc. My cpad did not work on the first boot, but after re-booting it was there.)

  Maybe the problem is that tosh_utils ( I think ) is designed for 2.6 kernel? Perhaps you are using 2.4? After I installed, I apt-got tosh_utils, and fnfxd (from Hoary universe), then all I had to do was add tosh_acpi to load at startup... Working like a dream and no lock-ups at all. 
 
  In my previous life with SuSe <>8.x, I was using kernel 2.4 and had to load several modules manually to get fnfx working, and the power management was not "really" supported....

Sorry for rambling- but hopefully the above will help you. 

I love Ubuntu -

---

### Post by SurreaL on 2005-02-28
First of all.. thanks for the replies everyone :)

This shouldn't have been a kernel issue, because Hoary installed w/ 2.6.10, which is the latest stable version.. And it wasn't a module thing, because lsmod shows toshiba_acpi as being loaded, so I'm frankly not sure why toshutils doesn't work :/

That being said, toshset *does* work..! I was able to install it after modifying my apt sources to include the hoary universe, and everything seems well. It still gave me an error basically saying that it preferred APM to ACPI, but it still seems to get the job done! I can adjust the fan/lcd brightness/everything else without problems.. so it's perfect :)

Now the only problem that remains is the freezing on shutdown/reboot :( I'm not sure what causes that, but from some searching I've seen that it doesn't seem I'm the only one who has the problem. I could always try to re-compile the kernel w/ APM support and try some of the compatibility options which I remember seeing in there, but frankly I don't want to break anything else by doing so.. for now I'll just put up with having to force it to shutdown 90% of the time :P

---

### Post by aev on 2006-01-04
Hi,

i have the toshiba_acpi.ko files and I added them in /etc/modules but lsmod doesnt show it loaded. Respectively toshset/fnfxd dont work. Any help pls? Also how do you start toshutils? Dum question from a newbie :) Thanks a lot.

---

