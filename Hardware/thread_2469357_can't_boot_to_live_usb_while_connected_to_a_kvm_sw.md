---
title: "can't boot to live usb while connected to a kvm switch"
date: 2021-11-26
forum: Hardware
---

### Post by ronjjjg8885 on 2021-11-26
hello

i've been trying to use a live usb of ubuntu while connected to my kvm switch but for some reason i couldn't.

do i must boot to the usb stick without being connected to the kvm?

a little problematic for me to disconnect it.

would appriciate a clarification.

i've even tried to unplug the mouse/keyboard dongle and insert to the comuter itself instead of the kvm switch.

the reason for testing with a live usb is to determine if the volume problem is because of my ubuntu or not.

the problem that i've is that whenever i lower the volume under 30 percent while connected to the kvm it's completely muted

please let me know

thanks

---

### Post by sudodus on 2021-11-26
For several years I used a KVM switch (for VGA video plus audio), and I had no problems with booting from USB and no problems with audio (at least no problems, that I could blame on the KVM connection). But now I don't use it, I have a direct connection via Displayport and/or HDMI.

It is possible that your KVM switch is causing problems. So even if it is a little problematic, I suggest that you disconnect it and test how things work when the computer is connected directly to the monitor.

---

### Post by ronjjjg8885 on 2021-11-26
hi and thanks
how do you use Displayport for multuple computers with one screen?
i've an hdmi kvm switch by blackbird.

i can try your suggestion tho i think it can be a bit problematic...

---

### Post by sudodus on 2021-11-26
I use Displayport for only one computer. The former computers connected via VGA were old desktop computers, and I sent them to the recycling station.

I have not tested any HDMI KVM switch, so I don't know if it is fully 'transparent' but it is easy to think that it can cause problems in some cases.

Maybe you can make a first test in a separate computer (maybe a friend's computer), that is not connected to any KVM switch, so that you know, that the Ubuntu system in the USB drive is good. After that it will be more worthwhile to disconnect the KVM switch.

---

### Post by ronjjjg8885 on 2021-12-03
so it seems it doesn't related to the kvm
i've tried it now

i've connected it directly to the computer and got this....

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289577&stc=1[/IMG]

(the mouse and keybaord are connected directly to the computer too)

---

### Post by sudodus on 2021-12-03
What do you mean by "my desktop computer has Ubuntu 20.04.3 LTS 64bit"?

- Is this the installed system or the live system or both?
- Is the installed system working well except the problem at 30% of the [audio] volume?
- Did you check with sha256sum that the downloaded iso file is good?
- What tool/method did you use to create the USB boot drive? Did you test it in another computer?

It may help, if you tell us more about the computer and the installed system (if Ubuntu or an Ubuntu community flavour). In order to show details about your computer, please [download and run the **[FONT=Courier New]system-info[/FONT]** script](https://github.com/UbuntuForums/system-info/). Let it upload the result to a pastebin and paste the link into a new reply here.

---

### Post by ronjjjg8885 on 2021-12-04
hi and thanks
i've the same ubuntu installed on the computer but i want to reinstall (i'm not very familiar with out to create clones of the system)

so it is installed system in which i want to reinstall with a life usb stick

except for the volume problem the system is ok. but i've many packeges that i've installed that i don't know which to remove and also i want to reinstall for using lvm this time. (i need to check if the volume problems occurs if i replace the cables but it's a bit hard to try to get to the cables for me.)

i haven't checked the sha256sum because it is somewhat complicated but i will make an effort to do it now.

for creating the usb boot drive i've used startup boot creator from ubuntu.
i haven't tested it on another computer but will now.

i've created the system info script
i don't know how to select it all and copy it to pastebin. i can only select the current screen.

what do i need to press for making it all selected?

edit:
the sha256sum ubuntu-20.04.3-desktop-amd64.iso made the same output like on the download section.

also. my other computer is giving the same results like my linux computer. the same error like i've posted in the screenshot.

so it is not the computer that causes the problem

---

### Post by ronjjjg8885 on 2021-12-04
ok
thank you for helping
it is now booting to the installation ok

i redownloaded the iso and made a usb disk with another thumbdrive

---

### Post by sudodus on 2021-12-04
I'm glad that you could solve your problem :-)

Just to make things complete I will answer/comment on a few items, that might be useful in the future.

> **ronjjjg8885 said:**
> for creating the usb boot drive i've used startup boot creator from ubuntu.
i haven't tested it on another computer but will now.

The Ubuntu startup disk creator is a reliable tool :-)
> 
i've created the system info script
i don't know how to select it all and copy it to pastebin. i can only select the current screen.

what do i need to press for making it all selected?

After an introductory dialogue, the system-info script will 'show the information' in the file viewer 'less'. This is for your eyes only, and contains some information, that should not be uploaded to a pastebin.

When you have scrolled through that information, please exit from the viewer 'less' by pressing the key 'q'. Then the script will create a file with filtered information, that is suitable for uploading to a pastebin, and if your computer has a suitable tool, the script will ask you if you want to upload the [filtered] information to a pastebin.
> 
edit:
the sha256sum ubuntu-20.04.3-desktop-amd64.iso made the same output like on the download section.

also. my other computer is giving the same results like my linux computer. the same error like i've posted in the screenshot.

so it is not the computer that causes the problem

> **ronjjjg8885 said:**
> ok
thank you for helping
it is now booting to the installation ok

i redownloaded the iso and made a usb disk with another thumbdrive

It seems to me, that there was a problem with the thumbdrive, and you solved it by using another one. Is this a correct conclusion?

In that case you can try to refresh the problematic thumbdrive by wiping the whole device, overwrite it with zeros. You can do that in a safe way with [mkusb](https://help.ubuntu.com/community/mkusb). If there are still problems with that thumbdrive, see [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035).

---

