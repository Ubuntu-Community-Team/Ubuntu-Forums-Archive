---
title: "cannot login to x after update, want to revert to vesa"
date: 2013-05-17
forum: Hardware
---

### Post by wabbalee on 2013-05-17
Hi

I updated my system yesterday (12.04) with synaptic (including nvdia-current) and now I get presented with kdm login screen. after entering credentials it comes back to the login screen. I have edited my xorg.conf file a million times and still no difference. System has been running smooth for ages, I have tonnes of software installed over time and it would take me ages to get it all back, not to mention my limits on downloads that will make it harder for me to complete if I was to start from scratch again.

There were some problems stated by synaptic but I was stupid enough to reboot and see what would happen.

now i want to revert back to whatever drivers (vesa?) 12.04 comes with out of the box and use 'addittional drivers' to fix the problem.

does anybody know how to do this? all I have is virtual terminals to work with.

thanks for reading my post

---

### Post by CatKiller on 2013-05-18
You can use apt-get on the command line to purge nvidia-current. Nouveau should get enabled on the next boot.

---

### Post by wabbalee on 2013-05-19
Thanks for your reply, after a day looking up all sorts of ways to get it back under command line, I started looking through my usb devices and found a back up from a few months ago that I have used and updated successfully. I did purge nvidia current before I posted this thread, but it made no difference which is most likely due to my lack of knowledge from tha almighty command line.

---

### Post by wabbalee on 2013-05-19
now I'd like to mark it {SOLVED} but i am not seeing how to do it..

---

### Post by CatKiller on 2013-05-19
The old easy way broke with the recent forum update. Editing the first post is the current workaround.

---

### Post by wabbalee on 2013-05-19
Thanks CatKiller,
One Love!

---

