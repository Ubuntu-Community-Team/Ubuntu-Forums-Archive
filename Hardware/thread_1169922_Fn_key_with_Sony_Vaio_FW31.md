---
title: "Fn key with Sony Vaio FW31"
date: 2009-05-25
forum: Hardware
---

### Post by lads on 2009-05-25
Hi there,

I recently acquired a Sony Vaio VGN FW31 and installed Ubuntu 8.10. Not surprisingly, the Fn key didn't work. The screen is set by default to full brightness, which makes working on Ubuntu more than 30 minutes per day an hazardous task.

After a few google searches I found this tutorial:

[http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/](http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/)

It consists in patching and recompiling the DSDT.dsl file and adding a sony-laptop module to the kernel. As is, this tutorial doesn't work for the FW3x series, but with hand editing the DSDT.dsl file it is possible to mimic the tutorial to the end, although the compilation of this file returns a few errors.

After rebooting the Fn key with F5 and F6 bring up a small menu with a bar the moves right or left, but the effect on the screen brightness is nill.

Is there any other way to get the brightness controls to work? Is it worth it to try to update to 9.04?

I wonder is why is it taking so long for Ubuntu to support Fn keys natively. I've been having similar problems ever since I tried Ubuntu on a laptop. For first time users this is a real impediment, what are the difficulties?

Thanks in advance for any help.

---

### Post by lads on 2009-05-27
Hello again,

After reading other websites I tried to run acpi_listen to make sure Ubuntu is getting the Fn inputs. Here’s what I got after pressing Fn+F5 and Fn+F6:

```
lads@MDK:~$ acpi_listen
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b

```

It seems to me that Ubuntu is getting the correct signals from the keyboard but is either ignoring them or failing to transmit them to the graphics card.

Any help? Thank you.```

```

---

### Post by ajmctaggart on 2009-05-27
Maybe I can help!

I recently got a Sony Z series Vaio...There is a patch to get brightness keys working.  The nice thing about this patch, you don't have to install it completely to test it...you can test it, if it doesn't work, just remove it.  

[COLOR="Red"]Again, this patch was not built for the FW specifically, but I'd like to see if it helps for the Launchpad group's documentation.

[/COLOR]

[http://www.basyskom.org/~eva/sony-laptop-zseries-0.9.tar.bz2]("http://www.basyskom.org/~eva/sony-laptop-zseries-0.9.tar.bz2")

Use archive manager to extract it, then read the README file to figure out how to make, and how to make test before actually installing...

Please let us know how this works, if it works at all...

Good Luck!

---

### Post by lads on 2009-05-27
Hi there ajmctaggart, thanks for your reply.

Opening the readme file, it starts by stating the following:

<blockquote>
This is an update to the sony-laptop kernel module for Z series laptop. This driver has been tested on a VGN-Z21VN/X. It can break other Vaio laptops.
</blockquote>

I'm a bit reluctant in using this patch in face of this. Have you ever tried it with an FW series? Please mind that the Fn+F6 and Fn+F5 do work and Ubuntu is getting their signals, as you can see from the output of the acpi_listen command. The problem is that the screen brightness is left unchanged.

Anyway, thanks for your help.

---

### Post by ajmctaggart on 2009-05-27
Ya that's why I suggested to do make-test before installing it...
No problem though, there are some other options...

1) [Sony-laptop Module]("http://www.linux.it/~malattia/wiki/index.php/Sony-laptop") 

2)  Add Screen Brightness applet to Menu Bar

3)  [Map the keys yourself]("http://ubuntuforums.org/showthread.php?t=400077") (This link be a bad thread to show the "how-to," you may want to search for a better way to do this)

Good Luck!

---

### Post by lads on 2009-05-27
Thanks once again ajmctaggart.

Fortunatelly for me egaistek from vaioubuntu.wordpress.com solved the issue by posting a specific version of DSDT.dsl for the FW31 series:

[http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/#comment-641](http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/#comment-641)

Community is everything :)

---

### Post by ajmctaggart on 2009-05-27
Sweet! Glad it's fixed...

---

