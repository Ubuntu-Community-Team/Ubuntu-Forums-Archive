---
title: "Keyboard and mouse sometimes does not work when startup"
date: 2009-05-22
forum: Hardware
---

### Post by code453 on 2009-05-22
Hello,

I'm having a problem with mouse and keyboard that does not work when ubuntu 9.04 startup. I cannot type the username for login and move the mouse around :(. But If I move the mouse around before the login screen appear, they work!!:)

Does anyone know how to solve this problem?
Please let me know

Thank you very much
Vanit

Note My system is 
--[ Software ]--
OS : Ubuntu 9.04 (kernel 2.6.28-11)

--[ Hardware ]--
Laptop : Dell Vostro 1310

---

### Post by Macchi on 2009-05-22
Hi Code453, (and by the way Welcome to the Ubuntu Forums!)

Please have a look at the link and text below since similar problems have been reported previously on the forum. Hope this will solve your problem. 

- The bad news is that apparently it is a kernel bug.

+ The good news is that there is a workaround for it. Most bugs are solved permanently after some time. Check this link:

[http://ubuntuforums.org/showpost.php?p=7222177&postcount=10](http://ubuntuforums.org/showpost.php?p=7222177&postcount=10)
(it is a good idea to keep an eye on that thread, and don't forget to report the bug!)

Anyway, to facilitate for you and for others I have copied the solution here:

>  Posted by user "FIRESOCK"
Hi!
We got exactly the same problem... so it's a kernel bug of ubuntu 9.04, because it's happening in the same laptop model in the same way.

I have tested some solutions that i have found in the forum and in the Internet and none of these have worked.

[...edited...]

Hey I have found the solution:

in the console:

gksudo gedit /boot/grub/menu.lst

In this file edit the kernel line and add in the end of this line this:
i8042.reset i8042.nomux i8042.nopnp i8042.noloop

It should look something like this:

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid d3383ae0-1621-4457-8138-7114fd0e3005
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=d3383ae0-1621-4457-8138-7114fd0e3005 ro quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop
initrd /boot/initrd.img-2.6.28-11-generic
quiet

Then in the kopt= line add in the end of the line the same. It should look something like this:
# kopt=root=UUID=d3383ae0-1621-4457-8138-7114fd0e3005 ro i8042.reset i8042.nomux i8042.nopnp i8042.noloop

Then save.

With these changes, it should be working perfect at startup.

Please let me know if it worked.

Have a nice day!
Last edited by firesock; 2 Weeks Ago at 06:38 AM.. Reason: I have found a solution 

---

### Post by kumarnum1 on 2009-05-29
Hello,

I tried this editing but didn't help :(

any other suggestions?

regards..






> **Macchi said:**
> Hi Code453, (and by the way Welcome to the Ubuntu Forums!)

Please have a look at the link and text below since similar problems have been reported previously on the forum. Hope this will solve your problem. 

- The bad news is that apparently it is a kernel bug.

+ The good news is that there is a workaround for it. Most bugs are solved permanently after some time. Check this link:

[http://ubuntuforums.org/showpost.php?p=7222177&postcount=10](http://ubuntuforums.org/showpost.php?p=7222177&postcount=10)
(it is a good idea to keep an eye on that thread, and don't forget to report the bug!)

Anyway, to facilitate for you and for others I have copied the solution here:

---

### Post by mbehdad on 2009-07-06
I have the same problem. My laptop is Dell Vostro 1510, and half the time, Ubuntu does not recognize its keyboard at the boot time :( Any solution?

---

### Post by Whatts on 2009-07-25
Hi,

I had the same problem, solution can be found here: [https://bugs.launchpad.net/ubuntu/+bug/334249](https://bugs.launchpad.net/ubuntu/+bug/334249)

Check the link for full details but in short: the line "i8042.reset i8042.nomux i8042.nopnp i8042.noloop" needs to be added to /boot/grub/menu.lst

---

