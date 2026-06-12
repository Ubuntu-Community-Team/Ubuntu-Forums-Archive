---
title: "Firefox and font issues"
date: 2008-11-30
forum: General Help
---

### Post by Dyonas on 2008-11-30
I've noticed this issue on more than one website so I'm sure it isn't just one site with a weird option causing this but I have no idea what to do about it.  The issue is that while most of the text renders fine a few distinct letters crop up that are what I can best describe as faded compared to the rest.  Specifically it seems to affect the letters K, R and X but there may be more I've not noticed yet.  I'm including a few screencaps from both these forums and another website mentioning poor Linux fonts.  I know they're not the greatest but it should show what I mean.  Granted, these aren't huge issues but it bothers me a lot and if there's a way to resolve it I'd be very grateful.

[[IMG]http://img385.imageshack.us/img385/383/fonts2kh5.th.jpg[/IMG]](http://img385.imageshack.us/my.php?image=fonts2kh5.jpg)

[[IMG]http://img89.imageshack.us/img89/6735/fontslb8.th.jpg[/IMG]](http://img89.imageshack.us/my.php?image=fontslb8.jpg)

---

### Post by kerry_s on 2008-11-30
that is common with sharp angles, they need alot of hinting to make them look straight, so they get a more smeared/grey look.

i once knew a fix for that where you make those certain letters blacker. i'll look around see if i can find those notes, but don't hold your hopes up, i don't use smooth fonts in normal text, only bold and italic, so i haven't seen those notes in years. your best bet would be to google for the fonts.conf fix.

here's what mine looks like:

---

### Post by Dyonas on 2008-11-30
Ah I see, so it's a known issue and not something I've magically done during my customising of the UI.  If you can find that info it'd be great but if not I'll live with it.

---

### Post by kerry_s on 2008-11-30
try some of this guys settings, he seems to cover most things:
[http://www.infinality.net/blog/?p=3](http://www.infinality.net/blog/?p=3)

if you don't have a .fonts.conf already you just need to make it: gedit ~/.fonts.conf

put this at the top:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
```

this at the bottom:
```
</fontconfig>
```

your settings go in between, you only have to restart the program to see affects, but remember it does affect the whole desktop, you just won't see that until you log out and back in.

this is what mine looks like, so you can get a idea of how it's suppose to look like. good luck.
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

 <!-- disable antialias for regular fonts -->
 <match target="font">
  <test compare="more" name="pixelsize" qual="any">
   <double>9</double>
  </test>
  <test compare="less" name="pixelsize" qual="any">
   <double>18</double>
  </test>
  <edit mode="assign" name="antialias">
   <bool>false</bool>
  </edit>
 </match>

 <!-- antialias bold fonts -->
 <match target="font">
  <test name="weight">
   <const>bold</const>
  </test>
  <edit name="antialias" mode="assign">
   <bool>true</bool>
  </edit>
 </match>

 <!-- antialias italic fonts -->
 <match target="font">
  <test name="slant">
   <const>italic</const>
  </test>
  <edit name="antialias" mode="assign">
   <bool>true</bool>
  </edit>
 </match>

</fontconfig>

```

---

### Post by Dyonas on 2008-12-02
Thanks again for the link, quite a lot of information there!  I don't know whether it's due to my messing with fonts or the Mac4Lin install and configuration but the fonts issue seems to be gone now.  It could be the fonts installed via that are more legible or something else I did but I'm not noticing the same faded letters any more.

---

