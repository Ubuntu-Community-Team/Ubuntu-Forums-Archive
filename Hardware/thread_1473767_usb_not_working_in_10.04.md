---
title: "usb not working in 10.04"
date: 2010-05-05
forum: Hardware
---

### Post by GregoryMA on 2010-05-05
After upgrading to lucid my usb ports no longer work.  They neither detect nor mount any usb devices.

Here is the output of lsusb (note that I have a usb device plugged into each of my usb ports):
```

gregory@box:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The output of dmesg | tail (again with two devices plugged in):
```

gregory@box:~$ dmesg | tail
[ 3515.412108] usb 1-2: new high speed USB device using ehci_hcd and address 32
[ 3515.552087] usb 1-2: device descriptor read/64, error -71
[ 3515.796108] usb 1-2: device descriptor read/64, error -71
[ 3516.012128] usb 1-2: new high speed USB device using ehci_hcd and address 33
[ 3516.152116] usb 1-2: device descriptor read/64, error -71
[ 3516.396109] usb 1-2: device descriptor read/64, error -71
[ 3516.612352] usb 1-2: new high speed USB device using ehci_hcd and address 34
[ 3517.036083] usb 1-2: device not accepting address 34, error -71
[ 3517.148085] usb 1-2: new high speed USB device using ehci_hcd and address 35
[ 3517.572077] usb 1-2: device not accepting address 35, error -71

```

This seems to be a common problem but I can't seem to get any closer to a solution.  Some kind of work-around or a way to manually mount devices would be greatly appreciated.

Thanks, Greg

---

### Post by j.daniel on 2010-05-06
**Hi,**

  Had a similar error trying to connect an USB memory, dmesg gave:

```
[10379.348053] usb 1-3: new high speed USB device using ehci_hcd and address 6
[10379.432157] hub 1-0:1.0: unable to enumerate USB device on port 3
```

  Found after a while the [[COLOR="Blue"]following page[/COLOR]]("http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/"): 

> 
Since Karmic doesn’t use ehci_hcd as a module, modprobe -r ehci_hcd no longer works. The module is compiled into kernel. To disable it execute the following commands in terminal:

```
    cd /sys/bus/pci/drivers/ehci_hcd
    ls
```

You will see a file with 0000:00:xx.x format. Execute the following command:

```
    echo -n “0000:00:xx.x” > unbind
```

Replace the xx.x with the numbers displayed on your file. It should disable the ehci_hcd.

Since you need to be root to run these commands (and you have the redirection above), if you try to do the following, you will fail

```
sudo echo -n “0000:00:xx.x” > unbind
```

...since sudo only applies to echo and not to unbind. Cannot remember the correct syntax for this but a simple way is to do (if you run gnome):

```
sudo gnome-terminal
```

and run the command there (I know, I know, this is WRONG! ...but it works...). You could put it all in a script and sudo-run the script also of course.

After this I could access my memory stick, but I got some weird access problems on an external USB harddrive, so I rebooted after I had the files I wanted.

Hope this helps.

Cheers!
/ Daniel

---

### Post by GregoryMA on 2010-05-07
I am afraid I got an error message when I tried.  Did you ever come across this?

```
root@box:/sys/bus/pci/drivers/ehci_hcd# echo -n "0000:00.13.2" > unbind
bash: echo: write error: No such device
```

---

### Post by dino99 on 2010-05-07
sudo apt-get update
sudo apt-get install -f
sudo update-pciids && update-usbids
sudo dpkg --configure -a

---

### Post by ubnewbie2 on 2010-05-29
> **dino99 said:**
> sudo apt-get update
sudo apt-get install -f
sudo update-pciids && update-usbids
sudo dpkg --configure -a

Tried that sequence - the third command reported this error

```
sudo update-pciids && update-usbids
Downloaded daily snapshot dated     2010-05-10 03:15:02
touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.

```

and it didn't fix the problem :(

---

### Post by j.daniel on 2010-05-29
> **ubnewbie2 said:**
> Tried that sequence - the third command reported this error

```
sudo update-pciids && update-usbids
Downloaded daily snapshot dated     2010-05-10 03:15:02
touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.

```

and it didn't fix the problem :(

Instead of 
```
sudo update-pciids && update-usbids
```

Break it up into two commands:
```

sudo update-pciids
sudo update-usbids

```

Should fix the permission denied error at least.

Cheers!
/ Daniel

---

### Post by ubnewbie2 on 2010-05-29
Yeah it did - I see what the problem was thanks.

Unfortunately, it didn't fix the USB enumeration problem though.

---

### Post by ubnewbie2 on 2010-05-29
> **ubnewbie2 said:**
> Yeah it did - I see what the problem was thanks.

Unfortunately, it didn't fix the USB enumeration problem though.


Aaah, problem solved.  It wasn't good old Ubuntu's fault really.  Bad firmware in the reader!  I flashed it with new firmware and now it works !!!

---

### Post by Bombenbach on 2011-01-17
> **GregoryMA said:**
> I am afraid I got an error message when I tried.  Did you ever come across this?

```
root@box:/sys/bus/pci/drivers/ehci_hcd# echo -n "0000:00.13.2" > unbind
bash: echo: write error: No such device
```
 
Without quotation marks ;)

```
root@box:/sys/bus/pci/drivers/ehci_hcd# echo -n 0000:00.13.2 > unbind

```Btw, the fix works good!

---

