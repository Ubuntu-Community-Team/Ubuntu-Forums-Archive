---
title: "Skype phone compatable?"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by bobbymcsteels on 2007-12-04
Ok i picked up a cheap skype phone the other day and I am tryin to get it working with my skype on ubuntu, it works fine in vista but havin a bit of trouble getting it to work in ubuntu. The phone is the magicbox voice 320
[http://www.dealclick.co.uk/review/12167750/Magic-Box-Voice-320-VoIP-Phone.php](http://www.dealclick.co.uk/review/12167750/Magic-Box-Voice-320-VoIP-Phone.php)

I have looked in the sound devices tab in skypes options and there are lots of channels/devices listed for both in/out-put but not sure how to identify which are which.
Anyone got any idea?
Thanx
Bobby

---

### Post by bobbymcsteels on 2007-12-04
anyone?

---

### Post by bobbymcsteels on 2007-12-06
wow still no answer

---

### Post by bobbymcsteels on 2007-12-12
any ideas?

---

### Post by christhemonkey on 2007-12-12
Upon plugging it in, what is the output of this command?:
```
dmesg | tail 
```

---

### Post by bobbymcsteels on 2007-12-13
Thanx for the reply
Ok bit of progress, I have found the phone in the skype settings(didnt pick it up previously) I can hear sound through it but its not picking up my voice when I talk through it.

I have set the sound out as Voice 320(hm:V320,0) which is working fine but Sound in I have set to voice 320(plughw:v320,0) but no joy, have tried also with both set to the same but still nothing, any idea?
Thanx in advance

---

### Post by christhemonkey on 2007-12-13
If you right click on the volume icon and go "Open Volume Control"

Then go to the recording tab and make sure nothing is muted and everything is selected and turned up.
Also try going "File" > "Change Device" and see if your skype phone is listed there.

---

