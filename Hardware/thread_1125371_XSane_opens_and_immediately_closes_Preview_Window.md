---
title: "XSane opens and immediately closes Preview Window"
date: 2009-04-14
forum: Hardware
---

### Post by StephenRGW on 2009-04-14
I have an Epson Stylus DX5000 All in One Machine and am running Ubuntu 8.04. I have no problem with printing.  The first time I scanned, everything worked fine.  Now when I go to scan, XSane detects the Epson, opens the Preview window and then immediately closes it, and when I choose to reopen it all by selecting Show preview from the Window menu of the Scan window all but the edges of the Preview window are completely blank.

Any suggestions for correcting this would be welcome.  Would reinstalling XSane do the trick?  If so, how do I reinstall it?

---

### Post by scarab on 2009-06-06
I have a HP4180 and the exact same problem.... usually I uninstall then reinstall Xsane and it returns to work for some time, then a week or so latter it occurs again.... any ideas would be really appreciated
cheers

---

### Post by StephenRGW on 2009-06-07
Since my original post I have learned how to uninstall and reinstall applications (hardly anything to learn!) and have tried it once with XSane without success.

But I will now try it several times.  I would put up with the inconvenience of having to do this regularly if it would mean I get the scanner to work when I wanted.

---

### Post by Thruston on 2009-07-10
I saw this symptom when I upgraded to 9.04. Apparently it is caused by junk in your user settings that does not get cleared properly when you upgrade xsane.

The quick fix is just to delete your ~/.sane directory.

1. Close xsane 

2. Delete ~/.sane ```
mv ~/.sane /tmp/.sane-old
```

3. Restart xsane

You will of course lose all your window position etc settings this way, so you may need to fish about in the old settings files...

Toby

---

### Post by StephenRGW on 2009-07-13
> **Thruston said:**
> I saw this symptom when I upgraded to 9.04. Apparently it is caused by junk in your user settings that does not get cleared properly when you upgrade xsane.

The quick fix is just to delete your ~/.sane directory.

1. Close xsane 

2. Delete ~/.sane ```
mv ~/.sane /tmp/.sane-old
```

3. Restart xsane

You will of course lose all your window position etc settings this way, so you may need to fish about in the old settings files...

Toby
Many thanks for this, Toby.  It looks very promising.  I will have to do a bit of homework on using Code before trying it out.

---

### Post by ionospheric on 2012-09-12
> **Thruston said:**
> I saw this symptom when I upgraded to 9.04. Apparently it is caused by junk in your user settings that does not get cleared properly when you upgrade xsane.

The quick fix is just to delete your ~/.sane directory.

1. Close xsane 

2. Delete ~/.sane ```
mv ~/.sane /tmp/.sane-old
```

3. Restart xsane

You will of course lose all your window position etc settings this way, so you may need to fish about in the old settings files...

Toby

I still have this problem under Ubuntu 12.04, and your recommendation solved the problem. Many thanks.

---

