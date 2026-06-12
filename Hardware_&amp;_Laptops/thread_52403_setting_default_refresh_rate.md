---
title: "setting default refresh rate"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by woedend on 2005-07-27
Hi guys.  I have a 17 inch hp v70s monitor.  The default on install was 85, which worked fine but had some very faint but ultimately annoying horizontal lines in the screen, most noticeably at the top.  I finally got them to go away by setting this value to 60, which it seems causes most people here problems but maybe thats what my monitor was made for.  Anyhow, when setting it to 60 it also makes the screen a bit smaller.  I can deal with this later.  The problem I get now is...upon bootup at the GDM its still at 85, which I can tell because it is full screen and I can see the lines.  After logging in, the monitor makes that noise(a click of sorts), blacks out, then my desktop comes up at the 60 hz, and an offsized screen.  So...I suppose, my question is, can I set it to just boot up, even at the gdm, to 60 hz?

---

### Post by mad_scientist03 on 2005-07-27
What does your xorg.conf file tell you? You should have lines for 'HorizSync' and 'VertRefresh'. What are those set to?

---

### Post by RKO on 2005-07-27
AFAIK, you need to setup custom modeline for your resolution to xorg.conf.. (I might be completely wrong though, I'm new to ubuntu too) To do this, you'll need to edit your xorg.conf ( /etc/X11/xorg.conf ) Find the monitor section, and insert your custom modeline there.. Use [this](http://koala.ilog.fr/cgi-bin/nph-colas-modelines)  to generate one.. Example from my xorg.conf below. 

```
# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5-96
    VertRefresh 48-160
    Option "DPMS"

ModeLine "1400x1050" 156.30 1400 1464 1784 1912 1050 1052 1064 1090 #75Hz
``` This might not be the "right" way to do this though, perhaps someone else will know better.. (I'm sure there is a _much_ simpler way) If not, give it a try. Worked for me anyways :)

---

### Post by dtfinch on 2005-07-27
In recent years, I haven't seen X obey the HorizSync and VertRefresh options. It seems to just probe the monitor and override my manual setting.

---

### Post by woedend on 2005-07-27
horiz is 30-70, vert is 50-120...already have added that.  Like I said, it does come up for me to 60 hz when ubuntu actually loads, but in the GDM  i think its called, the screen which you loging at, its at the other rate... in xorg.conf I did a search for the number '85'(default setting) and found nothing.

---

### Post by heimo on 2005-07-27
[QUOTE=woedend]horiz is 30-70, vert is 50-120...already have added that. Like I said, it does come up for me to 60 hz when ubuntu actually loads, but in the GDM i think its called, the screen which you loging at, its at the other rate... in xorg.conf I did a search for the number '85'(default setting) and found nothing.[/QUOTE]

I'm not sure what you want to achieve, but if you want to force refresh rate to 60Hz, I'd try:
 ```
     VertRefresh 60
```

---

### Post by sinbad782 on 2005-07-27
you can also throw a

dpkg-reconfigure xserver-xorg

as root in order to generate a new xorg.conf. Once you have answered all the questions, a ctrl-alt-backspace will then restart X with the new settings.

---

