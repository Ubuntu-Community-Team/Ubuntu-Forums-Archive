---
title: "Ubuntu and KVM Switches."
date: 2009-07-12
forum: Hardware
---

### Post by bunorama on 2009-07-12
Just curious.  Why would Ubuntu not ship working with KVM switches?

I've never had a problem with Windows, 98,2k,xp,Vista.... many different switches, different hardware.  always works.  It even works with THIS hardware with Win.

I've been reading peoples solutions for a couple hours, absolutely ridiculous.

This is a good example of why Ubuntu is NOT desktop ready.

---

### Post by tomdagreek on 2009-07-12
i dont understand why ur kvm switch would have problems...
i have a 5 year old compac kvm running 6 boxes...

---

### Post by darco on 2009-07-12
The only issue I ever had with a KVM switch is when switching back I would lose the extra mouse key functions. Unplug/replug would fix that.

darco

---

### Post by Hobgoblin on 2009-07-12
> **bunorama said:**
> Just curious.  Why would Ubuntu not ship working with KVM switches?

????

I've used Ubuntu with a KVM switch.  What make/model is it?  Does it rely on Windows drivers?

If it needs drivers to work then it's the switch which doesn't work with Ubuntu, not Ubuntu which doesn't work with the switch.

---

### Post by coffeecat on 2009-07-12
Over the past four years I have used 5 different KVM switches (of various makes - 4 vga, 1 dvi) and Ubuntu and other Linux distros have worked just fine with them all. The only real problem I recall is with Windows XP regularly freezing when switching from my Mac Mini with one Belkin KVM. Ho hum. :rolleyes:

So... if you need help, post details of your particular KVM switch and what is and is not working.

---

### Post by bunorama on 2009-07-12
TrendNet tk-207
[URL="http://www.trendnet.com/products/proddetail.asp?prod=105-TK-207K&cat=105"]http://www.trendnet.com/products/proddetail.asp?prod=105-TK-207K&cat=105
[/URL]
I have several keyboards, generic, eclipseii. all usb.
Tapping scroll-lock doesn't switch Ubuntu 904 to Xp, but it does go the other way.

It works with the button on the KVM itself.

Since the keyboard plugs directly into the KVM, I would guess the OS wouldn't matter, unless a driver tells the pc to send a signal back to the KVM to switch it.  But from reading the info on their site, no driver is needed.

I read that the KVM will switch not becuase of the key, but because the light on the keyboard changes, but that didn't work.  I was able to test this by setting up 2 USA layouts and setting the layout options to light the scroll lock LED when in an alternate layout.  Switching layouts lights the key but doesn't switch the KVM.

I was able to use keyboard shortcuts (which I think insatlled with Ubuntu) to assign calc to the scroll lock.  Still no switching the KVM but at least I can calculate how much time I've wasted on this.

I hope that's enough info...

---

### Post by coffeecat on 2009-07-12
First thing, your link says...

> Supports Windows 98/98SE/ME/2000/XP/2003 Server, **Linux**, and Mac OS... so if the KVM is not working to specification you have an issue to take up with either the manufacturer or the retailer. I downloaded the user manual and from that...

> Q5: How do I switch from one computer to another with the KVM switch?
A5: PC User: Push Buttons, Hot-Key Commands or Client Switch Utility
Mac User: Push Buttons
Linux User: Universal Hot-Key Commandsand

> If you have further questions, please contact TRENDnet&#8217;s Technical Support
Department.... which suggests that a call to Trendnet might be in order.

Curious that for MacOS, only the push button is mentioned. I wonder if there is a printing error and Linux should be the same. Either way, a call to Trendnet might clear this up.

Personally, I've never found hotkeys on KVMs to be reliable in any OS, so I always use the button on the KVM. Which seems to be working for you.

---

### Post by bunorama on 2009-07-12
Thanks.

---

