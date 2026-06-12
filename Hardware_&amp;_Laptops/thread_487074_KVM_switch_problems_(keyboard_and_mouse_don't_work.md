---
title: "KVM switch problems (keyboard and mouse don't work)"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by tfountain on 2007-06-28
Hi all. This may not even be an Ubuntu issue but I'm posting here as a last resort in the hope that someone will be able to suggest something:

I recently bought a 2 port KVM switch ([this Rextron one](http://www.aria.co.uk/Products/Peripherals/Switch+Boxes/2+Port+KVM+Switch+with+DVI?productId=21383)). I've hooked this up to my two PCs - one dual boots between Ubuntu (feisty) and XP, and the other just has XP installed. The KVM works fine on the XP-only PC, but neither the keyboard or mouse work at all when I switch to the Ubuntu/XP one. The display is fine on both.

The weird thing is, when the Ubuntu PC is intially booting, the keyboard works fine on the GRUB OS selection screen (I can scroll up and down the choices there), but as soon as I get to the Ubuntu (or XP) login screens there's no sign of life from either the mouse or keyboard.

I've tried a few obvious things:

* The reset/reinitialise button on the switch doesn't help
* It's not an issue with the KVM cables as I've tried swapping these around
* The cables are definitely plugged into the correct ports
* I've tried two different keyboards (both PS/2), and three different mice (and old PS/2 one and USB ones through an adapter)

And ruled out a few less obvious things that were the result of some extensive Google searching:

* The switch doesn't come with its own power, but I bought the optional power cable as well which hasn't helped
* Plugging a keyboard directly into the PC whilst it boots and then plugging the KVM keyboard cable afterwards didn't help

there are quite a few posts on these forums by people with KVM issues, but these seem to either be eratic mouse behaviour or problems with USB keyboards, whereas my problem is a little different.

I know the fact that the KVM doesn't work in XP either on the dual boot PC suggests this isn't an Ubuntu problem, but I'm wondering if something's going awry in ubuntu's hardware detection on boot, or if it's something grub-related I can fix somehow.

Any suggestions appreciated!

---

### Post by ripcrd on 2007-07-13
I have a similar problem.  Scroll lock 2x and up arrow should switch from Linux to XP.  I have a Belkin 2-port KVM to share a 17" LCD between Kubuntu and XP.  When I had Dapper, I had no problem switching between Kubuntu and XP, but since I upgraded to Feisty, I have problems.  I switch over to the Linux box during boot, the keyboard works during BIOS and GRUB menu (though GRUB goes by quickly), then after the kernel takes over, the keyboard goes dead.  I have had to plug a USB kb in to be able to run it.  I also have had a USB mouse on the same box.  I have never gotten the two to play nice with the keyboard.  Either Linux loses mouse or XP does, usually Linux.   I have previously given up on KVMs sharing between Linux and XP, but Dapper worked fine.   I can't remember if I did something special back when I loaded Dapper to fix this.

Someone in my LUG suggested adding acpi=off to the GRUB line.  Problem is, this motherboard is new enough that it should have ACPI and Linux should detect it.

Need some help here.  :confused:

"Somewhere there is a village missing an idiot."   :lolflag:

---

### Post by spelingchampeon on 2007-07-14
I am in the same predicament. I have a Lightwave 8 port KVM. Everything works with Windows and Dapper... but not Feisty. No clues as of yet...

---

### Post by aliasmailjunk on 2007-07-31
I have an IOGEAR USB KVM. Prior to reinstalling both my Windows and Linux machines. The KVM worked fine with 6.10 and windows. Now that I am back to Linux and upgraded to 7.04....the KVM doesn't work at all. I'm kind of at a loss. I may just go buy a smaller keyboard to place on my desk for the Linux machine, but I was really hoping to get my KVM working.

---

### Post by joesapo on 2007-10-23
Has there been any headway made regarding the KVM issues w/ the Linux kernel?  I'm tired of crossing my fingers all the time when I bring up a new Ubuntu box.

I thought 7.10 might fix this, but still no dice.

---

### Post by spelingchampeon on 2007-10-25
Update: I pretty much sat on this issue for 3+ month's or better. I just installed Gutsy (7.10) and I am typing on my KVM so my mouse and monitor work too. This is the very same motherboard/cpu and KVM combo that refused to work with Feisty (7.04). 

Why does it work with 7.10?? ..your guess is as good as mine. GL

---

### Post by ian_ryeng on 2007-12-06
hmmm....

well, at least im not alone with KVM issues. It seems odd however that it affects everyone's machines differently. For example, i am using a Belkin Flip. It works fine if i boot the Ubuntu box with the KVM switched to that box, everything will run fine until i switch to the other computer. When i come back i have no keyboard or mouse functionality. Further, i tried plugging another usb mouse in the ubuntu computer but that didnt work either. It seems that (in my case) the issue might be that ubuntu doesnt support hot plugging usb devices? 

Is there a way to configure ubuntu so that it will work with a usb mouse (and keyboard)  that is plugged in after startup? It seems to me that there should be, i just have no idea how to do it.

The strangest part about all this is that if i boot up and login, but dont startx i can switch between both computers with no issues! :confused:

So, if anyone knows how to enable/configure hot plugging in Gnome to even just get a usb mouse to be recognized and function after entering the dashboard it would be greatly appreciated.

---

### Post by John Franklin on 2007-12-13
I've also got a KVM problem. My device (Starview SV411) works fine with Windows and also worked with Dapper. Since upgrading to 7.10 (which I did incrementally through 6.10 and 7.04) the mouse has been erratic and unusable and the keyboard sometimes duplicates characters. The KVM is only about a year old. Why does Dapper work and not any version since? I've tried different mice and tracker balls but all the same.

---

### Post by phil_ on 2007-12-19
Hi All,

I have a similar problem. I am using an Avocent 16 port KVM. 

When I installed Ubuntu (7.04) the keyboard worked fine on the first boot screen, and in the BIOS, but as soon as it got to the  installation questions screen, it would not respond. I used a ps/2 keyboard to install and hoped the problem would resolve itself when the OS was installed... I have also tried using a 7.10 CD, and had the same problem with the install screen.

I can see that the KVM keyboard has power, because if I press any key on the keyboard, the scroll caps and num lock light simultaneously. The mouse on the KVM works fine!

<edit> We have several other machines running various strains of ubuntu connected to the KVM, and these work fine. The system in question is a Dell Poweredge 2500. I have upgraded it to the latest BIOS version.</edit>

I'm fairly new to ubuntu, so any troubleshooting tips  would be appreciated. Also, please specify which logs would be of any help to me here. I've checked dmesg, var/log/messages but am not really sure what to look for!?

Thanks in advance,
Phil

---

### Post by TechBob on 2008-02-04
Had similar problems with Iogear USB KVM (mdl GCS632U) and gave up.  Monitor switch works, but ANY connection to the USB port to KVM causes random response and repeat from keyboard (even after disabling keyboard repeat and BIOS support for USB keyboard)

My setup is a dual-screen XP workstation and use the 2nd monitor for Ubuntu 7.1 (AMD64) workstation.  I gave up and left KVM hooked up to XP and use it's keyboard to switch monitor 2 with a second compact PS2 keyboard and USB trackball for the Linux workstation. (Trying to reconnect with my "inner Unix" after 10 yrs away from SGI/Irix world...)

If anyone finds a KVM that works, I'd be interested - not to keen on trail & error purchases of multiple KVMs ... there is a certain appeal to having 2 keyboards, 3 input devices (including Wacom) and 3 monitors (inc. A/V monitor) - very "bridge of the Enterprise"... but a little crowded.

---

### Post by oldsoundguy on 2008-02-04
absolutely NO problems here with 7.10 on one box and XP on another.  Sharing WIRELESS keyboard and mouse .. 18" NEC LCD set to Portrait (thank you nVidia) AND Altec powered audio system .. using a D-Link KVM 121.  Took NO tweaking to get everything to work and switching between is NO problem.

BUT .. it uses the PS/2 connectors from the wireless receiver to the switch and at each computer.  USB is problematic, especially on the XP box.

---

