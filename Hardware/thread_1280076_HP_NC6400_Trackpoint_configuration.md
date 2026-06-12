---
title: "HP NC6400 Trackpoint configuration?"
date: 2009-10-01
forum: Hardware
---

### Post by cybic on 2009-10-01
Hello forum,
 
i'm a newbie here in forum - and btw. on ubuntu 9.04 also...

I have a problem with my nc6400: the configuration i'm able to change affects just the touchpad, but not the trackpoint :(

So i'm able to change the speed for the mouse-pointer for my touchpad, but not for the trackpoint...

Where could i configurate the speed for the trackpoint?

Mfg,

cybic

---

### Post by cybic on 2009-10-02
push

---

### Post by cybic on 2009-10-03
Push - nobody ever got this to work???

---

### Post by cybic on 2009-10-20
Same problem in Ubuntu 9.10 - I still don't know how to configurate my trackpoint. Every configuration change is for trackpad only!!!

---

### Post by cybic on 2009-10-25
Found a solution (on my own)...

Maybe it's interesting for somebody:

Make a HAL config-file **10-x11-input.fdi **

**Put this into:**

<?xml version="1.0" encoding="utf-8"?>
<deviceinfo version="0.2">
  <device>
      <match key="input.product" string="PS/2 Generic Mouse">
       <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
       <merge key="input.x11_options.EmulateWheelButton" type="string">3</merge>
       <merge key="input.x11_options.YAxsisMapping" type="string">4 5</merge>
       <merge key="input.x11_options.XAxsisMapping" type="string">6 7</merge>
       <merge key="input.x11_options.AccelerationProfile" type="string">2</merg$
       <merge key="input.x11_options.AdaptiveDeceleration" type="string">1</mer$
     </match>
  </device>
</deviceinfo>

Restart HAL and GDM

Superb - works fine for me :)

It seems the trackpoint is a PS/2 mouse and touchpad is synaptics for X11 ;)

---

### Post by totte on 2010-01-31
I am definitely a new at Ubuntu and Linux on my HP NC64000 so I was wondering where I should put this file and how to restart the applications you mention.

I am really excited about this solution of yours!!! 

Thanks!

/Totte

---

### Post by powerwave on 2010-03-03
Hey thanks for the solution, it worked for my Tablet HP 2700p as well!

@totte:
This is how it has worked for me. 
Use the following command in Terminal to edit and create the file in the correct directory: 
**sudo gedit ****/etc/hal/fdi/policy/10-x11-input.fdi** 
And following (cybic did a few typos):
```
<?xml version="1.0" encoding="utf-8"?>
<deviceinfo version="0.2">
  <device>
      <match key="input.product" string="PS/2 Generic Mouse">
       <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
       <merge key="input.x11_options.EmulateWheelButton" type="string">3</merge>
       <merge key="input.x11_options.YAxsisMapping" type="string">4 5</merge>
       <merge key="input.x11_options.XAxsisMapping" type="string">6 7</merge>
       <merge key="input.x11_options.AccelerationProfile" type="string">2</merge>
       <merge key="input.x11_options.AdaptiveDeceleration" type="string">1</merge>
     </match>
  </device>
</deviceinfo>
```Save it.

Logout and go to tty0 with CTRL+ALT+F1 and login

Then use this commands:
[B]sudo rm /var/cache/hald/fdi-cache
sudo restart hal
sudo restart gdm[/B]

That's it.
:popcorn:

~

---

### Post by handshake987 on 2010-12-10
I am new at Ubuntu (10.10) and i tried the solution on my hp 2510p.
But it seems so, that ubuntu 10.10 does not have an /etc/hal folder...

any ideas?

Sorry for my bad english...

---

