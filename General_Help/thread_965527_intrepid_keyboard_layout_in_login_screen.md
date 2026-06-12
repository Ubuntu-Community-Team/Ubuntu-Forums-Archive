---
title: "intrepid: keyboard layout in login screen"
date: 2008-10-31
forum: General Help
---

### Post by noremaku on 2008-10-31
In Hardy I had changed the system keyboard layout in xorg.conf to dvorak so that it would work in the login screen. In Intrepid it only loads the layout once I login as it did before I modified xorg.conf. I opened it and of course Intrepid no longer uses that file, but in the comments it said "replaced by HAL." So I did a search for filenames containing HAL, but none of the files, including hal.conf, had any mention of keyboard layout. I have also tried the "Apply system-wide" button on the keyboard preferences but that didn't do it either.

---

### Post by noremaku on 2008-11-03
*bump* Come on, I know I'm not the only one annoyed by this.

---

### Post by Songwind on 2008-11-07
I am having a similar issue.  My keyboard is Dvorak but it no longer allows switching to regular US.

---

### Post by Songwind on 2008-11-10
I hope you are still monitoring this thread for replies.  I got this figured out!  It's a matter of adding some lines to your preferences.fdi file.

I don't have time here at work to write a long post with the details and decent formatting, so for the moment I will just link you to [the tutorial I posted on my blog]("http://dragonseptarts.com/blog/?p=152").  You will do the same, but if you want Dvorak only you can leave out the ",us" and the whole option line for shift-switching.

Hope this helps.

---

### Post by noremaku on 2008-12-09
I can already toggle layouts, but my problem is it has qwerty as the layout for the login screen, and I can't use dvorak until I have logged in.

---

### Post by Songwind on 2008-12-09
noremaku:  Exactly.  If you use the tutorial I posted and modify your hal settings, it will give you dvorak at the login screen, too.

---

### Post by noremaku on 2009-01-22
Sorry, that simply didn't work. I tried your tutorial, still QWERTY before I log in.

---

### Post by Songwind on 2009-01-23
Hmm.  I didn't have any issue with this at all, unfortunately.

Are there any problems/errors in the Xorg.log in /var/log?

Eric

---

### Post by undefined117 on 2009-01-23
Thanks for writing the tutorial, Songwind! I've recently switched to colemak, and have been trying to get the keyboard layout enabled in KDM as well.

The code snippet as provided on your blog works, but when I try to change it to colemak like this:

```
  <device>
    <match key="info.capabilities" contains="input.keys">
    <merge key="input.x11_options.XkbRules" type="string">base</merge>
    <merge key="input.x11_options.XkbModel" type="string">pc105</merge>
    <merge key="input.x11_driver" type="string">evdev</merge>
    <merge key="input.x11_options.XkbLayout" type="string">colemak,us</merge>
    <merge key="input.x11_options.XkbOptions" type="string">grp:shifts_toggle</merge>
    </match>
  </device>
```

It stops working. I've tried restarting hal and the laptop itself to no avail. Does anyone know if I am using the wrong key for XkbLayout? I have a feeling that I'm missing something obvious...

---

### Post by Songwind on 2009-01-23
Colemak.com has some [examples]("http://colemak.com/Unix").

It looks like Colemak uses the "us" layout with additional symbols.  Maybe putting those keys in, rather than the ones I used for Dvorak would be more successful.

Good luck
Eric

---

### Post by undefined117 on 2009-01-23
ah I found by googling (I should've looked harder :) ) to use 'us(colemak)' like this:

```
  <device>
    <match key="info.capabilities" contains="input.keys">
    <merge key="input.x11_options.XkbRules" type="string">base</merge>
    <merge key="input.x11_options.XkbModel" type="string">pc105</merge>
    <merge key="input.x11_driver" type="string">evdev</merge>
    <merge key="input.x11_options.XkbLayout" type="string">us(colemak),us(intl)</merge>
    <merge key="input.x11_options.XkbOptions" type="string">grp:shifts_toggle</merge>
    </match>
  </device>
```

and it works! (Note that this works with 'us(dvorak)' as well; you could even change the 'us' part of that.)

---

### Post by Songwind on 2009-01-23
Ah!  Well spotted.  That's certainly clearer.  I think I shall have to make that change and update the site.

---

### Post by noremaku on 2009-05-02
I installed Jaunty from scratch, and chose dvorak in the installer, so now all my keyboard troubles are gone :)

---

