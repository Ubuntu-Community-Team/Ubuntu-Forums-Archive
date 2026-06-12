---
title: "hp laserjet 1020 printer not working"
date: 2013-05-18
forum: Hardware
---

### Post by Chelidze on 2013-05-18
Today I had to print a document but when I tried to print a file on ubuntu 13.04 I got this message first 

[IMG]http://i.imgur.com/JUfbUrV.png[/IMG]

That it is downloading and installing drivers but in ubuntu 12.10 and every versions of ubuntu I have used, when I would first time connect the printer it would start the commend line and ask me if I wanted or not to install the drivers. anyway after the reboot in the libreoffice writes print menu Hp laserjet 1020 was present but when I pressed print it didn't do any thing icon appeared in the top right corner and then it disappears. So does any one knows how to fix this 



Thank you in advanced

---

### Post by abacusreader on 2013-07-16
First you need to download and install HPLip 13.6 

[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)


run it in command line to install and follow on screen instructions.

At some point during installation it will pop up a box asking for root password - in this box if you enter your password even though you can do sudo, it will not accept it.

You have to set the root password for this window to work. (If you don't get this popup screen then it is highly unlikely your printer will print even though installation will be successful as per the script - if this happens rerun the script - there will be  a 2 successive questions as to whether check for driver updates and whether to download driver now - answer no for them in the command line this will result in this root password popup to appear)

Before you run the script, make sure to delete any auto detected printers in the System settings->Printers window. If not you will end up with 2 queues and it will not work.

Once you are done with the script, you will get a HP 1020 icon and check whether you can do a test print.

If test print is successful (paper prints ) then follow this bug report 

[https://bugs.launchpad.net/hplip/+bug/1197306](https://bugs.launchpad.net/hplip/+bug/1197306)
and install the patch file. If you don't do this, as soon as you reboot your printer, it will no longer work.  I just figured this bug report after almost a week of haggling with this printer and this bug

---

### Post by newbie-user on 2013-07-17
Running the following command will take care of the plugin problem:
```
hp-plugin -i
```

---

