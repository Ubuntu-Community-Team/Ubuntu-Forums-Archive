---
title: "BisonCam WebCam NB Pro Not working in Ubuntu 12.04"
date: 2012-05-28
forum: Hardware
---

### Post by yeehi on 2012-05-28
My webcam is not working. 

The webcam is integrated into my novatech 
nnb-801 Clevo W76TUN laptop.

I have tried to find out the exact model number but have failed.
I am testing Ubuntu 12.04 LTS Precise Pangolin in Virtual Box.

I have looked around quite a bit to try to find a solution but can't see anything.

I downloaded cheese and when I try to run it get the following error message:

```
(cheese:2244): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

** (cheese:2244): WARNING **: cheese-window.vala:1624: Error: No device found

```

I e-mailed the manufawcturer of the webcam, [Bison Electronics]("http://www.bisontech.com.tw/English/about.php"), to ask them to provide some support for Linux, especially Ubuntu but I haven't heard back from them. Their website says that they are an important manufacturer of webcams, so I am surprised there doesn't seem to be any support for them.

Please help me!

Thank you!

---

### Post by gordintoronto on 2012-05-28
Do you understand how to get access to USB devices in Virtualbox?

If you open a terminal and enter the command: lsusb
it should show you numerous USB devices, including the webcam, even if it doesn't work.

If it does not display the webcam, you need to work on your Virtualbox installation.

---

### Post by yeehi on 2012-05-30
Thank you for your help with this.
Here is the output of lsusb:

```
~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet

```

---

### Post by gordintoronto on 2012-05-30
I hope one of these will help:
[http://www.dedoimedo.com/computers/virtualbox-usb.html](http://www.dedoimedo.com/computers/virtualbox-usb.html) 
[http://www.howtogeek.com/howto/31726/mount-usb-devices-in-virtualbox-with-ubuntu/](http://www.howtogeek.com/howto/31726/mount-usb-devices-in-virtualbox-with-ubuntu/)
[http://askubuntu.com/questions/102749/how-to-activate-virtualbox-usb-devices-support](http://askubuntu.com/questions/102749/how-to-activate-virtualbox-usb-devices-support) 

I'm not sure how current they are.

---

### Post by yeehi on 2012-05-31
Thanks gordintoronto, that was a big help. I have the proprietary Oracle VirtualBox. I downloaded and installed the extensions for VirtualBox from their website. I also went into settings and configured the device filters for the webcam.

The webcam USB ID number is: 5986:0241 [0605]

(Thanks very much for your links which helped me find this useful usb ID!)

I went into devices and installed guest additions. VirtualBox can see my device correctly as a BisonCam NB Pro. The device BisonCam is ticked for use. I rebooted the virtual machine and I can still see it

lsusb lists the BisonCam as present.

I now try to launch cheese but get an error message which hangs my system:

(cheesee:2561): Gtk-WARNING **: Attempting to add a widget with a type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

Also, if i manage to get the BisonCam listed in lsusb again, how can I test it without using cheese?

Please help!

---

### Post by yeehi on 2012-05-31
Here is the output of lsusb:

```
 lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 004: ID 5986:0241 Acer, Inc BisonCam, NB Pro

```

The BisonCam is at last listed!

How do I test this webcam without using cheese, for the moment.
I don't want to risk crashing my system again and losing the configuration for my virtual machine which took a long time to set up.

---

### Post by yeehi on 2012-05-31
What can I do in Ubuntu 12.04?
Nobody is answering my other thread...

---

### Post by papibe on 2012-05-31
Hi yeehi.

You can test if it works as an input device for VLC.

You can use test the video input on Skype.

You can use web and flash based [meebo.com]("https://www.meebo.com/messenger") (using an IM account).

Just some ideas.
Regards.

---

### Post by Derek Karpinski on 2012-05-31
guvcview

---

### Post by gordintoronto on 2012-05-31
I'm sorry, I've never seen an error from Cheese. In my limited experience (three cheap or built-in webcams) it has either not recognized the webcam, or it has worked perfectly. In the case where it didn't recognize the webcam, I eventually got it working.

The "Digital Leader" webcam on my desktop was purchased in China for the equivalent of $10. Works great, although I need to do the "preload" thing for Skype.

---

### Post by neu2buntu on 2012-05-31
install ```
ffmpeg
``` , i use it like this to record from my inbuilt laptop webcam with this command , which outputs the recorded file to the /tmp folder ( *note you will not be able to view the output in realtime unlike with cheese )

```
ffmpeg  -sameq -f video4linux2 -i /dev/video0 -pix_fmt rgba -y  /tmp/out.mpg
```

or try command ```
gstreamer-properties
```  and under the video tab choose your webcam and press the test button.

---

### Post by idoitprone on 2012-05-31
Or go to some flash website that is full of webcam games

---

### Post by Hadaka on 2012-05-31
IF you have VLC
plug the cam into the usb port...if not built in then
at terminal...input


vlc v412:///dev/video0

its that simple.

---

### Post by lisati on 2012-05-31
Threads merged.
Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

---

### Post by Craige4107 on 2013-04-17
Try installing "guvcview" from the Ubuntu Software Center.  Make sure your webcam is turned on after you install..........Cheers....

---

### Post by Craige4107 on 2013-04-17
Try installing "guvcview" from the Ubuntu Software Center.  Make sure you webcam is turned on after install.  The webcam icon will appear on your apps bar once installed.  Just click on it.....cheers.

---

