---
title: "Turning Off Touchpad for Sony VAIO Laptop (EE Series)"
date: 2011-03-23
forum: Hardware
---

### Post by beadedbytes on 2011-03-23
I attempted to post my 1st thread yesterday but have not seen it inside the Hardware/Laptop Forum.  Therefore, I am posting my issue again.
 

 A couple of months ago, I purchased a Sony VAIO laptop model# VPCEE31FX.  I have not been able to figure out how to turn off the touchpad inside the Unbuntu (v10.0)/Linux environment.  (I should mention that I am a 'newbie' to the Linux world; to date, have been a diehard Windows user.)   
 

 I've searched some forums and the web for solutions.  For the options that I've attempted to implement, I have not had success in getting a resolution.  (Sometimes, I've felt there were 'steps' to the solutions that were not listed.)   
 

 Does anyone have any clear, complete ***'step-by-step'*** instructions for turning off the touchpad?
 

 Thank you in advance for any help.

 

 (Please let me know if this is not the right forum for this post.)

---

### Post by matt_symes on 2011-03-23
Hi

Open a terminal and type

```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled false
```

Does that disable it ?

Kind regards

---

### Post by beadedbytes on 2011-03-24
To matt_symes,
Thank you for the feedback.  Unfortunately, the command did not work.  However, inside the Ubuntu Documentation Community, there was information that did turn off my touchpad -- [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

One thing to note.  We had to modify the command that determines the device id to:  
xinput list | more.  Once the list appeared, we used the id# attached to 'general mouse'.

---

