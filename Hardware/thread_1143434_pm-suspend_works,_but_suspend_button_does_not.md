---
title: "pm-suspend works, but suspend button does not"
date: 2009-04-29
forum: Hardware
---

### Post by sir_blargh on 2009-04-29
Did a clean install of jaunty a few days ago.  The suspend function seemed to work pretty well (wireless didn't come back online, but a quick hack in /etc/pm/sleep.d/66wireless.sh fix that).  Then 1 or 2 days ago, there were a series of package updates including acpid and powermgmt-base.  Not sure if those packages are relevant, but now when I click on suspend, or press Fn+F4, suspend does not work.  The screen will go black, but never enters a suspended state.  I can't switch to another VT, nor can I get back to my GDM session.  At that point I have to power off and back on...so how can I retrieve any data as to what went wrong?

But here's the kicker -- If I run "sudo pm-suspend" it will suspend just fine.

Any ideas?

Thanks!

---

### Post by astoncade on 2009-04-30
I have exactly the same problem but I'm still on 8.04.  I'm stuck with the LTS version because 8.10 and 9.04 both don't work on my laptop for various reasons (8.10 just won't install and 9.04 has major grief with my wireless chip).

The machine is a Toshiba Satellite A200-27U.  I've had it working before but can't remember how I did it which makes it even more frustrating!

---

### Post by sir_blargh on 2009-04-30
Interesting.  I had come from 8.10 which didn't suspend at all, so was pleasently surprised when 9.04 suspended properly.  For a few days at least.

For reference my machine is an Averatec AV-3270.

Don't you hate it when you got something to work but because you only ever did you once, you can't remember?  I used to write these things down, but then I forgot where I put it.

---

### Post by sir_blargh on 2009-04-30
Ok, I hacked around a bit and now mine is working.  Hopefully this will help you too.

Because pm-suspend by itself worked just fine, I found how to pass the suspend command directly to HAL [here]("https://wiki.ubuntu.com/DebuggingGNOMEPowerManager").  When doing that, suspend did not work properly.  Looking at the [architecture]("https://wiki.ubuntu.com/PowerManagement#Architecture") of the whole ACPI / HAL / power management stuff showed that HAL could potentially be introducing some quirks when calling pm-suspend.  

Looking at [this]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/198808") bug report showed me how to figure out which quirks were being set by executing this code:

```

$ lshal | grep quirks
  power_management.quirk.dpms_on = true  (bool)
  power_management.quirk.dpms_suspend = true  (bool)
  power_management.quirk.vbe_post = true  (bool)
  power_management.quirk.vbemode_restore = true  (bool)
  power_management.quirk.vbestate_restore = true  (bool)
  power_management.quirk.vga_mode_3 = true  (bool)

```

On my system, an Averatec 3270, I assumed that it was using the default quirk file, /usr/share/hal/fdi/information/10freedesktop/99-video-quirk-default.fdi.  By editting that file as root, I first tried setting all of the values to false.  I then reset hal (sudo /etc/init.d/hal restart) and then verified all values were indeed false (lshal | grep quirks).  I then hit the suspend button, but it again failed.

After some trial and error, I found that for my machine to work I needed all values to be true, except for "vga_mode_3".  Here's my current & correct configuration:

```

  power_management.quirk.dpms_on = true  (bool)
  power_management.quirk.dpms_suspend = true  (bool)
  power_management.quirk.vbe_post = true  (bool)
  power_management.quirk.vbemode_restore = true  (bool)
  power_management.quirk.vbestate_restore = true  (bool)
  power_management.quirk.vga_mode_3 = false  (bool)

```

So...there you have it.  Hopefully that will help!

---

### Post by akin1231 on 2009-08-27
So what exactly does the button on the gnome desktop do?  
I want to run a script before the suspend initiates.  I also want this script to run if suspend initiates due to a idle timer.

---

### Post by astoncade on 2009-10-02
Finally figured out what I did to solve the problem last time.  It's probably quite crude but it works perfectly every time.

My reasoning was that the command "sudo pm-suspend" does the job properly so I needed to find out what Ubuntu was doing differently when I used the suspend button.

Turns out that if you remove or comment out all the clever code that someone has written in the file "sleep.sh" and replace it with the simple command "pm-suspend" then it all just works.

I'm sure there's a good reason but it makes me wonder why someone went to the trouble of writing all that code?
PS I'm now running Linux Mint (a variant of Ubuntu) if that makes any difference.

---

