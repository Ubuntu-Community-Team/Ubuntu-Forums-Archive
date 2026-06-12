---
title: "support from Tripp-lite usb-serial adapter"
date: 2015-03-01
forum: Hardware
---

### Post by darioman on 2015-03-01
I have a usb serial adapter # usa 19hs  and can't find a thing on there site or the forums.  Gosh I dislike companies that print on the box works with pc/mac/linux...the joke on me

---

### Post by tripp98 on 2015-03-02
when you plug it in and open your software (i normally use gtkterm)  i run it from terminal sudo gtkterm.  click on configuration then at the bottom i have the usb to serial adapter.

to see if it is working open a terminal 
sudo tail -f /var/log/syslog
plug the usb adaptor in.  should show activity in syslog.  if the part at the top doesnt work post the output from syslog and someone here may be able to assist you further.

---

