---
title: "internal bluetooth not working"
date: 2008-08-26
forum: Hardware
---

### Post by MEGAMANULTIMATE on 2008-08-26
My XPS M1210 has internal bluetooth. At least, the BIOS says that it exists. Ubuntu, however, seems to think differently. However, no matter how much I try and find a way to activate it, nothing works. The LED on the keyboard stays dark, and my cell phone cannot detect anything besides my roommate's computer upstairs. Is there anyway to fix this? Any help at all would be appreciated.

---

### Post by Crafty Kisses on 2008-08-26
At the bottom of this page Troubleshooting

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by MEGAMANULTIMATE on 2008-08-27
Thanks for your reply. I followed your link as you suggested, and was disappointed since I run Hardy, not Gutsy (which is the error listed). Are there any other suggestions you have? I tried hcitool and those commands as well.

---

### Post by IntuitiveNipple on 2008-08-27
I suspect the Bluetooth module (usually TruMobile 355) isn't installed. If it doesn't show up in the output of lsusb that pretty much confirms it. In most Dell's the Bluetooth module is connected on the internal USB.

I answered someone else recently who has a Dell with no Bluetooth module and pointed them to where they can get the internal one for US$20 - [take a look at that thread](http://ubuntuforums.org/showpost.php?p=5663862&postcount=3).

---

### Post by MEGAMANULTIMATE on 2008-08-27
I'm sorry, but I don't really see what that solves. Are you saying I'll have to pay for more hardware to get this to work?

---

### Post by jordan420 on 2008-10-25
anybody solved this yet?

---

