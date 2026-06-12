---
title: "Asus Crosshair II Formula compatibility?"
date: 2008-09-15
forum: Hardware
---

### Post by Scucci on 2008-09-15
Mobo compatibility question.

Working on building a computer for college. I'll be overseas for atleast 4 years so I'm going a little overboard on building it because I need to make sure it can do anything I need it to do, hardware-wise.

I've picked out the motherboard I want, [Asus Crosshair II Formula]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131292") <-- Newegg Link. But I can't find any real information on the board, ever looked through the stickied posts here and the stuff on the wiki ([https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport")) Even Googled to find some reliable information... can't find anything.

Is there anyone out there using this board or KNOWS someone using this board that can help and give a thumbs up or down on if this board will be fully recognized by Ubuntu or not?

Here's my full saved "[wish list]("http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=9395686&WishListTitle=Yep")" at newegg for the rig. I'm pretty sure everything else will work, but everything else hinges on the motherboard question.
 
Any help will be very much appreciated.

---

### Post by darkjesus898 on 2008-09-23
There's a strange issue with the sata controller on the board but all you need to do to fix it is pass the kernel parameter "pci=nomsi".  

When you go to install hardy, push F6 and type that, without the quotes, at the end of the line there and proceed to install.  Note: I seem to be able to install successfully without this option but I figure use it to be safe anyways.  

Once hardy is installed, before you do ANYTHING, push alt+F2 and run "gksu gedit /boot/grub/menu.lst".  With the file open, search for the line "#kopt=root=UUID=....." there will be some big long hexadecimal string followed by "ro".  After ro add "pci=nomsi".  This will ensure that when your kernel is updated this option still gets passed to the kernel. 

Scroll down near the bottom of the file and fine your current kernel, should be after "## ## End Default Options ##".  Here you'll see "title Ubuntu....", what you are interested in is the kernel line.  Again you'll see the "root=UUID=" followed by hex and then "ro", once again add "pci=nomsi" here and do the same for the recovery mode below.  Immediately reboot and enjoy your hardy installation as normal.  

Other thoughts on the matter would be make sure you know what you are getting into with the 780a chipset, they have strange video corruption issues.  This is apparent to me only in Vista Ultimate x64, I haven't had an issue with it in ubuntu.  Hope I'm not too late in responding and that is of use to you.

Alex

---

