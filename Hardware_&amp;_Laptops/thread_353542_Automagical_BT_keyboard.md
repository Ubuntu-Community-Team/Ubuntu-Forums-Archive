---
title: "Automagical BT keyboard"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by L14UX_1NS1D3 on 2007-02-04
Hello.
Recently I was digging around and found my old MX900 keyboard, mouse, and bluetooth hub.
And outlandish popped into my head; "why don't I use this with linux". (gasp)!
before you all keel over and die thinking about this massive undertaking, the very first time I plugged the bt usb hub in the computer IT WORKED !
I got up and did a little victory dance about my computer but after I shutdown the computer and turned it on the next day my awesome automagical keyboard wasn't so automagical anymore.:cry: 
I went to see if I could manualy fix the problem. When I ran hcitool scan I was able to connect and even see the connection status but it still didn't work.](*,)  
I loaded the modules for bluetooth hub services and keyboard.
At boot I am able to pres ESC on the bluetooth keyboard to choose to boot up in recovory mode or some other options but once I get a prompt of any kind it stops working.
I am absolutely stumped as to what the problem might be.
PLEASE RESCUE ME !!   [-o<

---

### Post by L14UX_1NS1D3 on 2007-02-07
Hello again
 I am typing to this post from my bluetooth enabled keyboard. yay!
I found the problem I needed to set the bluetooth hcid.conf pin line to 0000
and enable hid devices with sdptool add hid.
This is such an ease to use the keyboard.
Ubuntu has come along way since the last time I'v used anything bluetooth with linux.
now that I have my computer hooked up to a tv with my nvidia card. I can use the keyboard as a remote!
cheers!! :popcorn:

---

