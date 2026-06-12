---
title: "Right alt and ctrl keys don't work in Edgy"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by Twiggy794 on 2006-11-02
I was running an Edgy upgrade before and recently did a fresh install, but now when I try to use my rightmost alt and ctrl keys on my laptop, they don't work at all.  The left ones work just fine.  Anybody know what could be up?  I've tried fiddling with the keyboard layout settings in GNOME with no luck.

---

### Post by bstock on 2006-11-05
I have a similar issue. Control works fine on the right, but not the Alt key. 

I did find a solution though. If you run 'xmodmap' from a terminal, you can see that it says 'mod5' is assigned to the Alt_R key. If you run this command:

xmodmap -e "remove mod5 = Alt_R"

That seemed to take care of it for me. Now all you need to do is set that up to run every time you run ubuntu. 

Go to System -> Preferences -> Sessions
Go to the Startup Programs tab
Click 'Add'
Copy and paste the previous command into the text area and click OK.

That should take care of the alt key. If you go to terminal and just run 'xmodmap', you can copy and paste the results and I can see what I can do about your control key.

Just FYI, I have a Logitech G15 USB keyboard. I don't know if this is a problem specific to this keyboard or not.

---

### Post by Twiggy794 on 2006-11-06
Thanks for the reply, I think I'm seeing what's up here but I'm unfamiliar with xmodmap so I'm not terribly sure how to go about adjusting this.  I did a quick xmodmap to check the output, here's what I got: ```
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d)
mod2        Mode_switch (0x5d),  Mode_switch (0x71),  Mode_switch (0x74)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  Mode_switch (0x71),  ISO_Level3_Shift (0x7c)

```
Seems that I have Alt_L specified twice, where I assume one should be an Alt_R?

---

### Post by bstock on 2006-11-06
Alright. After some more research and playing around, I think I found a solution. If you run 'xev' and look at the results when you push the right Alt key, it outputs:

```

KeyPress event, serial 32, synthetic NO, window 0x3e00001,
    root 0x186, subw 0x0, time 3193017024, (167,-14), root:(1234,563),
    state 0x10, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

While the left Alt key gives:

```
KeyPress event, serial 32, synthetic NO, window 0x3e00001,
    root 0x186, subw 0x0, time 3193324833, (759,352), root:(767,421),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


```

Notice with the left alt key, it says keycode 64 = Alt_L. If you look at the right alt, it says keycode 113 = ISO_Level3_Shift. I don't know wtf that is, but it's wrong...

Now from terminal we can run 'xmodmap -pke' to get a list of what keys our keycodes are assigned to. You should see similar results. We only really want to look at keycodes 64 and 113, since those are what we're dealing with.

keycode  64 = Alt_L Meta_L
keycode 113 = ISO_Level3_Shift

So, all we should need to do is assign keycode 113 to Alt_R right? That's easy enough. Run the following:

```

xmodmap -e "keycode 113 = Alt_R"

```

Now lets make sure the changes took effect. Run 'xmodmap -pke' again and take a look at keycode 113. You should now see:

keycode 113 = Alt_R

Success. Go to your browser, navigate through a few pages and try Alt_R+left and Alt_R+right to see if it's working.

Now we want to set this so it works every time we reboot. Should just have to add it to our sessions.

Go to System -> Preferences -> Sessions
Go to the Startup Programs tab
Click 'Add'
Put in xmodmap -e "keycode 113 = Alt_R" and click OK. Reboot and try it out.

You can probably remove the last command I said to enter, since that didn't seem to work. Let me know how it goes.

---

### Post by kungfoofool on 2006-11-14
I'm working on a Dell Inspiron 6000 and I have the same problem. I tried your code and unfortunately it didn't fix it. When I run xev, it does show that I'm hitting Alt_R but it doesn't do anything.

Neither of my alt or ctrl buttons on the right side of the keyboard work. Has anyone else had any luck with this?

---

### Post by bignate on 2006-11-27
I am having the same problem.  Dell Inspiron 9400.  Tried mapping the right alt key to no avail.

---

### Post by hellmet on 2007-01-02
Same problem here.. 
Anyone filed a bug??
I am on Intel 915GAV

---

### Post by nsleiman on 2007-01-02
same here :(

---

### Post by bignate on 2007-01-02
Sorry forgot I posted this here...

I just came up with a workaround.  Although there are many ways to accomplish this,  I created a shell script to set up my environment when I log in...and one of the lines in it fixes this issue.

in ~/.startup.sh:

xmodmap -e "keycode 113 = Alt_R Meta_R"

Then I added that to my login session:

System->Preferences->Sessions: Choose the Startup Preferences tab and add the script.

Not elegant, but it works.

---

### Post by jgubes on 2007-01-02
I assume you're in Gnome.  Have you tried this out in KDE?  It doesn't seem to be working for me.

---

### Post by bignate on 2007-01-03
Yeah sorry, I didn't mention that.  I am not familiar with KDE, I would guess it has a similar facility.

Alternatively, you may be able to add a ~/.xinitrc, and put those commands there, or the global xinitrc (/etc/X11/xinit/xinitrc).  I didn't test that either of those will work, but other distros I have used will source the users xinitrc.

---

### Post by jgubes on 2007-01-03
Sorry, let me explain why it's not working first...and since you're not familiar with kde, you probably won't be able to help...but maybe somebody reading this will be...

I ran the xmodmap command from terminal that you gave earlier.  It succesfully reassigned the right alt key...but I still don't have proper functionality for it.  When I go into the keyboard shortcuts setup and assign a shortcut using the right alt key, it registers as "ALT" but it won't record as a shortcut.  The left alt works fine.  Further, shortcuts that I assign using the left alt key aren't working with the right alt key.

I suspect this might have something to do with "X11" rather than xmodmap because when I go into the "Modifier Keys" tab, Alt_R still isn't mapped to mod1.  Anybody know how to change X11-mod mappings?

---

### Post by P235 on 2007-02-04
Hello, has anyone attempted this solution?

[https://launchpad.net/ubuntu/+source/xorg/+bug/63365/comments/4]("https://launchpad.net/ubuntu/+source/xorg/+bug/63365/comments/4")

I am somewhat unsure as to how to fix this problem myself and would like to know if there is a straightforward and informative solution for newbs out there?

EDIT:  Found it

[http://www.ubuntuforums.org/showthread.php?t=287318&page=2]("http://www.ubuntuforums.org/showthread.php?t=287318&page=2")

---

### Post by everdred on 2007-02-23
> **P235 said:**
> Hello, has anyone attempted this solution?

[https://launchpad.net/ubuntu/+source/xorg/+bug/63365/comments/4]("https://launchpad.net/ubuntu/+source/xorg/+bug/63365/comments/4")

Works perfectly for me. Thanks for the link!

---

