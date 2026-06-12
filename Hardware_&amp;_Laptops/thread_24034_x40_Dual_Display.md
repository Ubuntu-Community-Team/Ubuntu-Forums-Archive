---
title: "x40 Dual Display"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by kabanta on 2005-04-05
Hi,

I have been unable to solve the following problem on my IBM x40.

I would like to connect an external projector/display and have it mirror what is shown on the laptop display.

I assume this should work with FN-F7 -- is that correct? (ie, cycling through: laptop-only, external-only, and mirroring.)

- Are there particular files/drivers I need to have installed? If so, which?

- Any specific changes to internal files? (I've seen comments about this in the context of other x40/ubuntu questions.)

(I'm running under Hoary with the latest updates.)

thanks.

---

### Post by daniels on 2005-04-05
Grab the i855-crt package, and run 'sudo i855crt on 1024x768@60' (or something).

---

### Post by kabanta on 2005-04-05
Hi Daniel,

Thanks for the quick reply; yes, that worked. Relief! :-)

A couple of quick things:

- In case it will be useful for others, I will describe how to use
  your shell script in a bit more detail; feel free to add comments if
  something is specific to me.

  - Once the second display is connected, type the command: 

    sudo i855crt on 1024x768@60

    (or some other display-resolution)

  - This command does not enable FN-F7 -- it actually invokes the
    mirroring itself. 

  - For me, the first time I invoke this command (during a given
    session), both displays are shown with some video garbage across
    the top of the display. To solve this:

     a) Type FN-F7 a couple of times (to restore display to laptop)

     b) Invoke shell-command again.

  - Cursor doesn't seem to be mirrored on second display (which I
    consider a feature :-))

---

### Post by kabanta on 2005-04-05
[QUOTE=daniels]Grab the i855-crt package, and run 'sudo i855crt on 1024x768@60' (or something).[/QUOTE]

Oops -- my other comment/question seems to have vanished from my previous reply:

There is now a small, white square occluding the second display. It
  is up in the left-hand corner of the display and covers the Ubuntu
  "applications" menu item (and items below). I remember seeing a
  posting about this somewhere, but haven't been able to find it again
  (I don't remember if anyone posted a solution).

Any suggestions?

thanks.

---

### Post by daniels on 2005-04-05
Try 'i855crt on swcursor 1024x768@60'.  If you want your videos and stuff to go to the CRT instead of the LCD, put 'overlaycrt' just after 'swcursor'.

---

