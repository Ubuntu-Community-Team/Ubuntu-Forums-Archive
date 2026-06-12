---
title: "worng keyboard layout in login Logitech media Keyboard"
date: 2011-04-29
forum: Hardware
---

### Post by uxbridge on 2011-04-29
Hello
I have just upgraded my Ubuntu 10.10 to 11.04 and an annoying small problem arose.
My PC has a Logitech Media Keyboard with Italian layout (IT).
Italian is QWERTY, but during login the layout is evidently a QZERTY so I have to invert w and q typing. After having done that and having entered the system the layout is fine, plain QWERTY Italian as I can check in the "keyboard" section. There is no other keyboard layout installed apparently.
I have sourced information about QZERTY. It is unusual layout associated sometimes to Apple.
Indeed some time ago I tried to install the Apple Keyboard on Ubuntu 10.10 but that was a disaster so I switched back to the Logitech Keyboard.
But while 10.10 was using IT QWERTY login, I cannot understand why 11.04 uses QZERTY, maybe something about the Apple keyboard is still left into the system and the upgrade had brought forward the small issue.
If I go to the "keyboard" section within Ubuntu control panel, I see the IT layout, I can check all of the keys and they are fine, and my keyboard is appropriately selected, so I would not know what to do. I read maybe I have to do something with XORG.CONF, but my file is very small and contains nothing about the keyboard. 
Can anybody help me please?

Grazie/Thatnks in advance

---

### Post by fballem on 2011-04-29
Not sure if this will work, but assuming that you are using Unity, then this may solve your problem.

1/ Select the Keyboard application from the Applications menu.
2/ Select the Layout tab.
3/ See what keyboards are included there.
4/ From what you have described, the correct one should be Italy US keyboard with Italian letters, which should be included on the list. If it is not on the list, then add it by selecting the Add button and following the instructions on the next screen.
5/ Remove any keyboards from the list that you are not going to use. For example, if you are not going to use the AZERTY keyboard, then remove it from the list.
6/ Make sure that keyboard you want as default is at the top of the list. On my list, the US keyboard is on top.
7/ When you are done, select the button to Apply System-wide. You will be asked for your password.
8/ When you are all done, select Close, which will close the keyboard application. From that point, the correct keyboard should be used by default.

I hope this helps,

---

### Post by uxbridge on 2011-04-29
thank you.
No, the layout of my keyboard is ITALIAN with ITALIAN letters, not US. I had already tried before the "apply globally" but without success.

---

### Post by uxbridge on 2011-04-29
but maybe I have found the real problem.
If I restore the default setting of the keyboard I end up with the "Apple aluminium Keyboard". This has a wrong layout.

So it appears to me that at the login the system likely takes the default keyboard and then use the wrong layout. Once logged in it uses the correct layout. 

Does anybody know how to change this default setting to a QWERTY keyboard?

---

### Post by uxbridge on 2011-04-29
sorted out!

sudo nano /etc/default/keyboard

chaged: XKBMODEL="applealu_ansi"
into:      XKBMODEL="pc105"

and the problem is gone.
Thank you to everybody anyway for your time and help.

---

