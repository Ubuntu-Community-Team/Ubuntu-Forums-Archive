---
title: "Optical mouse + KVM + Ubuntu 510 + windoze"
date: 2006-02-24
forum: Hardware &amp; Laptops
---

### Post by Tomlin on 2006-02-24
After 3 days straight, I'm convinced THIS WON'T WORK!!!!

All I wanted to do was swap my Intellimouse for an optical mouse. I have an IOGEAR GCS14 PS/2 4 port KVM switch. I have a windoze 2000 machine, windoze 98 machine, Ubuntu 5.10 machine and a Damn Small Linux machine all running. The KVM in NOT powered. I first tried a Logitech optical mouse (cheap - $15). It has a USB-PS/2 adapter. I haven't found ANY optical mouse w/PS/2 connector.

The 2000 machine performed a "page back" in IE 6 and Firefox 1.5 when moving the wheel "up", but the Ubuntu and DSL machines worked fine. DSL worked as is, while the Ubuntu machine needed the xorg.conf file tweaked. If I plugged the mouse into ANY 2000 machine USB port, it worked fine, so I figured it was a power issue. I tried an MS optical mouse, and a Logitech "Click!" optical, with the same results.

2) I tried a Belkin OmniView F1DB104P 4 port KVM powered switch next. The 2000 machine now worked fine, as did the DSL machine, but Ubuntu REFUSED to cooperate (sort of). It worked until I switched to another machine and back again, then the cursor went haywire and moved aound the screen starting programs, popping up windows, etc. I had to CTRL-ALT-BACKSPACE, then CTRL-ALT-DELETE to reboot. When it came back up, it worked fine UNTIL I switched to another port and back again, then it became erratic. Again, this happened with ALL the optical mice (2 Logitech and 1 MS).

Is it POSSIBLY an issue with the USB-PS/2 connector? Has anyone had any success with:

ANY optical mouse, THRU ANY KVM switch with BOTH windoze and Ubuntu 5.10?

I searched the forums and that's how I got the mice to work in Ubuntu originally.

Thanks,

Tomlin

---

### Post by majikstreet on 2006-02-24
I dunno much, but I'll tell you one thing:
The newestish firefox 1.5 has a huge bug made by the developers in about:config.
Here's how to fix it:
type about:config in the address bar
type mousewheel.horizscroll.withnokey.action in the filter bar
right click on the thing that appears, choose modify
change 2 or whatever to 0
then click OK or whatever
then exit firefox
then start firefox
all fixed :D

---

### Post by wetland on 2006-02-24
Hi Tomlin

I also have a kvm switch. The logitech 700 mouse I use works fine until I switch to another machine. When I switch back to my kubuntu box I do lose some functionality in my Logitic 700mouse . I have searched for an answer to this problem and have not found an answer. It seems that certain types of mice on a KVM switch have problems like this or other problems. If I reboot the kubuntu box all is well. If you find an answer to this problem I would also be intrestred.

---

### Post by Tomlin on 2006-03-19
Well I found a solution (but it wasn't cheap). The consensus is, its a "power" issue. The adaptor doesn't pass the power needed for the laser to work correctly. I'm guessing the USB-PS/2 adaptor was at fault - not a faulty connector, I tried several.

Anyway, I bought an IOGEAR MiniView extreme 4 port hub. It uses ALL USB connectors and comes with 4 cables (proprietary :cry:  ). Then I bought a new USB keyboard.

Everything worked out of the box, except the scroll wheel on the Logitech "Click" mouse. But, by changing a line in the xorg.conf file from:

Option "Protocol" "PS/2"

to:

Option "Protocol" "ExplorerPS/2"

I got that to work also.

Bottom line - KVM = $150, new keyboard = $30.

One nice thing about this KVM box is that it has 2 extra USB connectors on the back to allow the sharing of peripherals. I plugged my scanner in and can use it from ANY of my 4 machines.

---

