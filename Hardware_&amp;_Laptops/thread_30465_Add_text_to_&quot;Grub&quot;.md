---
title: "Add text to &quot;Grub&quot;?"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by veronica84 on 2005-04-28
I have been trying to set up my Dell D505 with Ndiswrapper for a couple of weeks now and i am close, but no cigar yet. I have just read this following compatability-Ubuntu write up for the Dell D505 and I have no earthly idea how to add anything to the bootloader.

[[CENTER]*I]Modem (Conexant D480 DMC V9.x) and Firewire not tested. For the WLAN (Broadcom Dell 1450 a/b/g) I've used ndiswrapper  [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) with windows driver. After it, adding "acpi=noapic" to grub, made ubuntu recognize WLAN and sound card.*[/I][/CENTER]

Does anyone know how to do this?

Thanks,

Veronica xx

---

### Post by nad on 2005-04-28
At the grub boot selection menu, highlight the selection that you wish to edit with the arrow keys, then press 'e' to edit. Now, highlight the line that you wish to edit (this will be the long boot line) and press 'e'. add whatever options you wish to the end of this line (it seems that you want acpi=off and noapic) separated by a space, then press enter, and  then 'b' to boot with these options this time.

When you have a configuration that suits your purposes, you may wish to make the change persistent across reboots. In order to do this you need to edit the file /boot/grub/menu.lst .
There are some instructions in the file itself. Please post back with your results, and additional questions.

---

### Post by veronica84 on 2005-04-28
Thanks Nad! :)

Is it supposed to be acpi=noapic or apci=noapci? Might be a typo and I would like to avoid wrecking my shiny new Ubuntu OS :)

Thanks!

Veronica XX

---

### Post by nad on 2005-04-28
The syntax is I wrote (these are two separate options often used with a via chipset) and you are not going to hurt ubuntu with non-persistent changes like this. The ability to modify your boot parameters per boot is a feature often used for testing.

---

### Post by veronica84 on 2005-04-28
Okay! I added apci=noapic to the end of the sentence at Grub (with a space before apci=noapic). However it does not seem to have worked. 

When I do "modprobe ndiswrapper" i get 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Growl...........

When I do "ndiswrapper -l" I get 

bcmwl5 driver present : hardware present

But there is no Wlan0 in my "networking" GUI. I would greatly appreciate any tips. I have been at this for 2 weeks now:) and it is fun but it would be nice to get it working.

Thanks,

Veronica XX

---

### Post by nad on 2005-04-28
The two options you wish to use are; acpi=off  and the second; noapic separated with a space.

---

### Post by veronica84 on 2005-04-28
Okay cool, going to reboot into Ubuntu and try it now. Will let you know in 5 mins:)

---

### Post by veronica84 on 2005-04-28
No luck:( 

I am out of ideas now. Perhaps I should re-install ndiswrapper and try again? I have done that 3 times and it does not seem to have worked. I even tried re-installing Ubuntu and starting from scratch a couple of days ago.

Any help would be greatly appreciated.

:)

Thanks!

Veronica XX

---

### Post by nad on 2005-04-28
I've been single mindedly helping you with your grub issue. After rereading your posts (and bear in mind that I am not familiar with the ndiswrapper module) I note that you are getting a operation not permitted error. Out of curiosity, try two additional boot options: noexec=off  and  noexec32=off .

---

### Post by veronica84 on 2005-04-28
Thanks for your help Dan! Your a star. Now to try this new course of action. I live in Hong Kong anf Have just called in sick to work so I can spend the day playing with this:)

I will try the 2 "e" reboots and let you know how it goes.

:)

Veronica XX

---

### Post by veronica84 on 2005-04-28
AAAHHHHHHHH! Okay. I tried the noexec=off and noexec32=off but with no luck. Then I removed Ndiswrapper and reinstalled the 1.2rc1 version. Did very well until I tried to modify the debian rules as per the HowTo on this site. I am getting a no such file or directory response.

Would it really kill the guys at Dell to write a Linux driver? I mean, would it hurt them in some way?

:)

Thanks, I am going to keep on trying:) Any ideas will be welcomed and tested.

Veronica XX

---

