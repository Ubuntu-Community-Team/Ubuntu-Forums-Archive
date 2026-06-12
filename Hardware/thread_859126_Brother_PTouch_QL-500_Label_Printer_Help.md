---
title: "Brother PTouch QL-500 Label Printer Help"
date: 2008-07-14
forum: Hardware
---

### Post by LakeWind on 2008-07-14
Has anyone been able to get the Brother PTouch QL-500 Label Printer working with 8.04? Supposedly it works with the ptouch drivers for most people (various distro's but haven't found it working with Ubuntu 8.04) but I can't get it working. I've followed the instructions located here:

[http://openprinting.org/show_printer.cgi?recnum=Brother-QL-500](http://openprinting.org/show_printer.cgi?recnum=Brother-QL-500)

The printer apparently installs and is shown as an option under my printers however, nothing ever prints. I send labels to the printer and nothing happens. The job just stays in the print queue forever until canceled and cleared. 

Any suggestions for getting this printer up and running properly would be greatly appreciated.

Thanks in advance!

:confused:

---

### Post by LakeWind on 2008-07-15
Still can't get this working... Can anyone help please?

Thanks

---

### Post by jonibo on 2008-09-19
This is off the top of my head as I saw something like this a while back.

Edit this file:
/etc/cups/ppd/QL-550.ppd

Search for 'rastertoptch' in this file and replace it with the complete path to the executable '/usr/lib/cups/filter/rastertoptch'.

I have this in my /etc/cups/ppd/QL-550.ppd
$ cat QL-550.ppd | grep raster
*FoomaticRIPCommandLine: "gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=cups %A%Z -sOutputFile=- - | /usr/lib/cups/filter/rastertoptch dummyjob dummyuser dummytitle 1 &apos;%B&apos;"

I don't know if that will help you or not, but it's worth a try.  If it works for you, please try to submit a bug report somewhere (Launchpad???).

Good luck!

---

### Post by gwalborn on 2009-02-13
THANK YOU!  Adding the full path to the ppd file made a world of difference.  I had searched all over the Internet and you post helped the most.  I am still having a problem with the margins and centering, but I've got a chance to work that out now that I'm getting SOME output.  Thanks again, you're a life saver.

Gary Walborn
[email]gwalborn@gmail.com[/email]

---

