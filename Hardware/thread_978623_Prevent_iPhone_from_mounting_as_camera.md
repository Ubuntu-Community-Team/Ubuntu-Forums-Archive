---
title: "Prevent iPhone from mounting as camera"
date: 2008-11-11
forum: Hardware
---

### Post by TrueLens on 2008-11-11
I have an iPhone 3G that I connect to my computer and then sync via VirtualBox.  Every time I plug the phone it Ubuntu sees it as a camera and mounts it also asking if I want to import photos.  This prevents VirtualBox from being able to lock the device and I have to go and unmount it before the virtual machine can use it properly.

I believe I need to blacklist the iPhone however my searching has not yielded a solution.  Can anyone point me in the right direction?

Thanks!

---

### Post by TrueLens on 2008-11-15
Any ideas?

Thanks!

---

### Post by pumrum on 2008-11-18
bump -- i am experiencing the same problem. I use my iPhone through VMware, and would like to prevent my Ubuntu host from mounting it as a camera. I have already done:


   1.   Click Places > Home Folder
   3. Click Edit > Preferences
   6. Click the Preview tab
         1. Set Show thumbnails = Never
         2. Set Preview sound files = Never
   7. Click the Media tab
         1. Check Never prompt or start programs on media insertion
         2. Uncheck Browse media when inserted
   8. Click Close to save the preferences


this prevents any other usb storage devices from being opened or polled, but not mounted. is there a way to keep ubuntu from mounting the iphone (or any other digicam) as a camera?

---

### Post by sirzubov on 2009-02-19
I had this same issue.  I'm running a Windows VM and didn't want the host OS grabbing the device.

From what I can tell, there seem to be two devices for the iphone:
```

hal-device | less

```
[LIST]
[*]piped to less because the output is rather long
[*]search for "Apple"
[*]I used the value of "info.udi"
[LIST]
[*]make sure to grab for both devices
[/LIST]
[/LIST]

Then create a file like /etc/hal/fdi/policy/10-noiphone.fdi ("noiphone" is arbitrary...you can name it whatever you like) with the following:

```

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
    <match key="info.udi" string="$info.udi1">
       <merge key="info.ignore" type="bool">true</merge>
    </match>
  </device>
  <device>
    <match key="info.udi" string="$info.udi2">
       <merge key="info.ignore" type="bool">true</merge>
    </match>
  </device>
</deviceinfo>

```

[LIST]
[*]where $info.udi1 = first info.udi value from hal-device search
[*]where $info.udi2 = second info.udi value from hal-device search
[/LIST]

You can really use a combination of match keys, but I used info.udi because it was the most specific (I think you could do it by using just usb_device.serial to set info.ignore on both devices).

Hope that helps.

Cheers,
Philip

---

### Post by pumrum on 2009-02-19
Philip-

This is exactly what I was looking for. Worked perfectly... Thank you!

-ben

---

### Post by TrueLens on 2009-02-20
That solution does indeed work perfectly!  Thanks for your help!

---

### Post by frobie192 on 2009-04-04
I did this however now virtualbox does not seem to be able to access the phone.  Any ideas?

---

### Post by TrueLens on 2009-04-04
Do you have the version of VirtualBox installed that supports USB devices?  Does it show up in the list when you click on the usb icon at the bottom of the Virtualbox window?

---

### Post by frobie192 on 2009-04-11
It does show up but its greyed out and does not let me choose it.

---

### Post by TrueLens on 2009-04-12
Are all the devices disabled?  Do you have the latest version of Virtualbox (2.1.4)?

I found this thread that has instructions on how to get USB devices working in Virtualbox, however they suggest these steps are no longer needed in the new version.

[http://ubuntuforums.org/showthread.php?t=1015763&highlight=virtualbox+usb]("http://ubuntuforums.org/showthread.php?t=1015763&highlight=virtualbox+usb")

---

### Post by frobie192 on 2009-04-27
Yea everything is greyed out.  I even tried a USB memory stick.  I upgraded to 2.2 and its the same thing.

---

