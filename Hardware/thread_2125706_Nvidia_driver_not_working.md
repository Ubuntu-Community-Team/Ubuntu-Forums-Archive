---
title: "Nvidia driver not working??"
date: 2013-03-14
forum: Hardware
---

### Post by sdowney717 on 2013-03-14
I uninstalled then reinstalled still it says it is not working
see screen shot

I have run nvidia config and the xorg.conf file exists

---

### Post by papibe on 2013-03-14
Hi sdowney717.

Did you restart after installing the driver? If not, do so, and let us know how it goes.

Regards.

---

### Post by sdowney717 on 2013-03-14
sudo reboot twice

---

### Post by sdowney717 on 2013-03-14
I am showing synaptic with it installed and all.

Do I need to purge the driver and get it from nvidia instead of software center?

---

### Post by ManamiVixen on 2013-03-14
What is you computer model?

---

### Post by papibe on 2013-03-14
Could you post the content of the xorg log?
```
/var/log/Xorg.0.log
```
Please paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/") and post back the link.

Regards.

---

### Post by sdowney717 on 2013-03-14
Ok, I fixed it.

I installed the 310 experimental driver instead of the 304 driver.
Then I pulled the plug on power off.

It then booted up with the driver working.
So I dont know if it was the unplug or the 310 driver or what else.

I used some  ppa for the 310 driver instead of software center.

---

