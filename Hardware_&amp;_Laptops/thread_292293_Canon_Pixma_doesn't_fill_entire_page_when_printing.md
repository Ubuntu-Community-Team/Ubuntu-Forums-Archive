---
title: "Canon Pixma doesn't fill entire page when printing"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by reubano on 2006-11-03
Hi, I have a Canon Pixma MP500 running on edgy64 (had same problem with dapper64 also). The printer works but it does not fill the entire page on the printouts (i.e. it only fills in about 1/3 of the page from the top left corner). I tried using the alignment script from the linuxprinting site but that didn't fix the problem. I also tried converting the rpm canon drivers from the linux site but that didn't work (I guess it is only for i386). Has neone else faced this problem? And if so how did you fix it? Thanks!

---

### Post by Hrugaar on 2006-11-04
Hi,
I have the Canon MP600, i found the same problem. The TurboPrint drivers work well but you have to pay for them if you dont want a watermark. Alternatively you could try writing your own driver, this is what i tired. But i can only get it printing properly in black and white, colour is messed up.

Ru

---

### Post by reubano on 2006-11-04
hmmm, that sucks. I read on some of the printer threads that some people tried drivers from some japanese site. Do you know anything about that? Or, is there a way to make the linux canon rpm drivers work for amd64?

---

### Post by m94mni on 2007-01-11
Can anyone of you tell me what you did to make the printer output anything at all?

I have an MP600, and I can't get it to print anything... I've tried to alien the Canon RPMs, I tried the japanese debs, I've even tried the free Turboprint drivers. The Canon drivers and the Turborint drivers recognized the printer, but no test page gets printed.

---

### Post by DoctorMO on 2007-01-11
There is a Canon Pixma poll that I filled in to get canon to support the drivers more. the people you want to talk to are:

Canon (Your country here)
Gutenprint (For free drivers)
Turboprint (For non-free drivers)
Canon jp for some pixma drivers (non-free)

---

### Post by m94mni on 2007-01-11
I've tried all these options. There seems to be some kind of setup issue - the printer is detected, but I can't get a test page.

---

### Post by budgie9 on 2007-01-11
Being as you have not got any helpful replies I thought I would offer some suggestions.
If you search the forums for my name you will find several posts I have placed re Canon printers These may help you.
 I am aware that there are some further lib files that are required by some printers but what I can't say other than those I know and have mentioned in other posts.

Secondly, try opeining the printer driver properties and check the DPI of the printer for those that are getting smaller than full page 
images. You may be printing at the wrong resolution.
If any of you get the printer working PLEASE repost and tell others.

---

### Post by m94mni on 2007-01-29
Found the problem --- user "lp" was not in group "plugdev"

Running

sudo adduser lp plugdev

fixes the issue, and I can now print....!

---

### Post by anne on 2007-02-21
Same problem here, any solutions yet?
I did try to change dpi in printer option without any changes to the size of the text printing. All still compressed up in the left corner.

---

### Post by sylvilagus3 on 2008-01-26
Same problem...anyone has solution to the problem of MP600 not filling the entire page?

---

