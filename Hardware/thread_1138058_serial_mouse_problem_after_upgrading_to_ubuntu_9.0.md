---
title: "serial mouse problem after upgrading to ubuntu 9.04"
date: 2009-04-26
forum: Hardware
---

### Post by trldp on 2009-04-26
I just upgraded from ubuntu 8.10 to 9.04. After the upgrade my serial mouse doesn't work, anymore. Even 'cat /dev/ttyS0' doesn't give any output. Is there anything I can do to make it work again?

---

### Post by KhurramM on 2009-04-26
First things First:

Is your Mouse working? Check cables.

If OK. Then on the gdm just try unplug mouse for 10 sec , and the re-plug it back.

Hope this works.

---

### Post by tute on 2009-04-27
I'm having exactly the same problem.

Before I could make  serial mice work doing either:

[LIST=1]
In /etc/X11/xorg.conf:

```

Section "Input Device"
       Identifier "Configured Mouse"
       Driver "mouse"
       Option "Device" "/dev/ttyS0"
       Option "Protocol" "Microsoft"
EndSection

```[/LIST]

[LIST=2]
(From [http://www.faqs.org/docs/Linux-mini/3-Button-Mouse.html#s3](http://www.faqs.org/docs/Linux-mini/3-Button-Mouse.html#s3)):
```
ln -s /dev/ttyS0 /dev/mouse
```
[/LIST]

No one works now. The weird part is that the link ttyS0 -> mouse diesn't show up when I reboot.

Also lost in here...
Regards.

---

### Post by trldp on 2009-04-28
> **KhurramM said:**
> Is your Mouse working? Check cables.
My mouse works perfect on my debian and my (old) kubuntu 8.10 system. Only on my Ubuntu 9.04 it doesn't work. The cables are OK

> If OK. Then on the gdm just try unplug mouse for 10 sec , and the re-plug it back.No, doesn't work either :(

---

### Post by noirwrit on 2009-04-30
I've tried a slight variation on your method two above and it works for me:

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "Mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/ttyS0"
    Option        "Protocol"    "Auto"
EndSection

This is from a fresh install on a 32-bit Intel machine.  The mouse doesn't work during the login screens and there's a slight pause after the appearance for the desktop before it becomes active, but it works just fine afterwards.

I had two issues I couldn't resolve on my 64-bit AMD machine after upgrading and so I started over from scratch on that one.  They were: 1) The sound quit working even with PulseAudio removed (interestingly, it always worked when tested, just not inside other software).  and 2) "Hey, your index is corrupted!  Wanna, re-index?  It might take a while."  "Sure."  "Hey, your index is corrupted! . . ."

---

### Post by tute on 2009-05-02
Wow, it worked!
Didn't work with Protocol Auto, but with your lines and "Protocol Microsoft" it got working!
Thanks, now I can use my computer! :)

---

### Post by knoid on 2009-05-27
I had the same problem but enabling the lines I was using in xorg.conf didn't work for me.

With the help of a friend I was able to fix it by creating a text file named '10-mouse.fdi' in /etc/hal/fdi/policy/ and putting the following in it:

```
<?xml version='1.0' encoding='UTF-8'?>
<deviceinfo version='0.2'>
  <device>
    <match key='info.capabilities' contains='input.mouse'>
      <merge key='input.x11_driver' type='string'>mouse</merge>
      <merge key="input.x11_options.Device" type="string">/dev/ttyS0</merge>
      <merge key="input.x11_options.Protocol" type="string">ThinkingMouse</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
      <merge key="input.x11_options.CorePointer" type="string">On</merge>
      <merge key="input.x11_options.Buttons" type="string">4</merge>
      <merge key="input.x11_options.ButtonMapping" type="string">1 2 3 4</merge>
    </match>
  </device>
</deviceinfo>
```

The crucial line seems to be ```
<merge key='input.x11_driver' type='string'>mouse</merge>
```

It wouldn't work until I got that line in there.

---

### Post by Coburn on 2009-08-04
I'm using 9.04 on an old A31 Thinkpad.  Following the community docs HowTo plus a tweak or two I've gotten a serial mouse to work as a second pointer -- until I close the lid.  Then I have to use inputattach.  Using your fix makes inputattach not work any more for me.  I tried modifying it to match my xorg.conf, too.  Except I have two pointers configured, one with CorePointer and another with SendCoreEvents; I think the XML is merging things incorrectly.  How do I target the operation to put things where they belong?

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "Device" "/dev/ttyS0"
Option "Protocol" "Microsoft"
Option "Emulate3Buttons"	"true"
Option "SendCoreEvents" "true"
EndSection

```
```

<?xml version='1.0' encoding='UTF-8'?>
<deviceinfo version='0.2'>
  <device>
    <match key='info.capabilities' contains='input.mouse'>
      <merge key='input.x11_driver' type='string'>mouse</merge>
      <merge key="input.x11_options.Device" type="string">/dev/input/mice</merge>
      <merge key="input.x11_options.Protocol" type="string">auto</merge>
      <merge key="input.x11_options.CorePointer" type="string">On</merge>
      <merge key="input.x11_options.Buttons" type="string">4</merge>
      <merge key="input.x11_options.ButtonMapping" type="string">1 2 3 4</merge>
      <merge key='input.x11_driver' type='string'>mouse</merge>
      <merge key="input.x11_options.Device" type="string">/dev/ttyS0</merge>
      <merge key="input.x11_options.Protocol" type="string">Microsoft</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
    </match>
  </device>
</deviceinfo>

```

---

### Post by Fitch on 2009-10-24
I'm a complete newbie to Linux in any form.
I have a Pentium 2 that I thought I'd learn on.
So far, I've learnt that Ubuntu doesn't work on it.
I have a Genius EasyTrak "tracker ball" type with 3 buttons, needless to say
it's a serial rodent, and again, needless to say, it doesn't work.
I've tried the xorg.conf and the various differences listed, to no avail.
I even tried typing in the 10-mouse.fdi, but I apparently don't have permission to save it.
The internet doesn't work either by the way, so I'm using another computer (Windows XP) to tell you about it.
I have a router (192.168.1.1) which is the gateway to the internet, but I have no idea how to tell Ubuntu, and certainly don't have a clue without the mouse.
 
So I have 3 problems in all:
no mouse
no internet
no file permission.
 
Any help would be greatly appreciated.
Yours in anticipation
Fitch.

---

### Post by agharbeia on 2009-10-25
You need to be running the editor in the root context, i.e. using *sudo* or *gksudo*, in order to be able to save to a system directory.
So try something like "sudo nano"

---

### Post by Fitch on 2009-10-25
Ok, I used "sudo"

Every time I switch on, I now go CTRL ALT F1, log in, type in:
"sudo inputattach -bare /dev/ttyS0", then CTRL ALT F7
and the mouse works.
Shall I just use one of the ideas above to make it automatic?

P.S. As luck would have it, the NIC died, which was why there was no internet.  I can now gladly tell you that I'm typing this using the "errant" computer with new NIC installed.

Almost there....

---

### Post by agharbeia on 2009-10-26
I had the same problem.

Below id my /etc/hal/fdi/policy/10-mouse.fdi file in case it would be of help. You may need to replace "IntelliMouse" with "bare". but try it as is first.

Remember to save it using root power.

[HTML]<?xml version='1.0' encoding='UTF-8'?>
<deviceinfo version='0.2'>
  <device>
    <match key='info.capabilities' contains='input.mouse'>
      <merge key='input.x11_driver' type='string'>mouse</merge>
      <merge key="input.x11_options.Device" type="string">/dev/ttyS0</merge>
      <merge key="input.x11_options.Protocol" type="string">Intellimouse</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
      <merge key="input.x11_options.CorePointer" type="string">On</merge>
      <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
    </match>
  </device>
</deviceinfo>[/HTML]

---

### Post by Fitch on 2009-10-26
Hi again.
 
I loaded root, but don't know how to use it.
I'm really stuck in that I can't save the file to \etc\hal\fdi\policy
After a while I managed to save it to my home directory, but it has a padlock on it and will not go where needed.
I still dont have file permissions.
As I said earlier, I'm a complete newbie, so have no idea of how to get around Linux at all.:(

---

### Post by agharbeia on 2009-10-26
Sorry for not being clear.

I'll assume that you created the file 10-mouse.fdi in Windows and saved it to a USB to transfer it to Ubuntu.

After booting Ubuntu, copy the file from the USB to the proper location:

sudo cp */media/usb/*10-mouse.fd /etc/hal/fdi/policy/10-mouse.fd

where */media/usb/* is the path where your USB is mounted.

Issuing: ls -l /etc/hal/fdi/policy/10-mouse.fd  should return:
-rw-r--r-- 1 root root 627 2009-05-31 14:15 /etc/hal/fdi/policy/10-mouse.fdi

if not, then fix ownership by issuing: sudo chown root:root /etc/hal/fdi/policy/10-mouse.fd
and fix mode by issuing: sudo chmod 644 /etc/hal/fdi/policy/10-mouse.fd


If you're using the emergency repair terminal then you're already logged in as root and don't have to use "sudo", but it won't hurt.

---

### Post by Fitch on 2009-10-27
Cheers for that! :D
 
Well, I'm learning, be it ever so slowly...
 
I've sent Julie off to find an idiot's gude to Linux - aptly named.
 
But at least the mouse works!!
 
The only change was from your "Intellimouse" to "microsoft"
1 annoyed Julie ('cos I took so long), and we need another jar of coffee.
 
Thanks for that.
 
Unfortunately for you, I may be using this forum quite often....

---

### Post by agharbeia on 2009-10-27
Savour this feeling! You'll soon be missing it once you've become an expert.

---

### Post by beren on 2009-10-27
Hi,

due to fortunate circumstances I was in the opportunity to reinstall Ubuntu 9.04 last Sunday - and today again. This is on a desktop that I use for trying out some new functionality - and I then do a clean install.

However - to the point of this topic - last Sunday my mouse was not recognised for the first 10 minutes. After trying out some older PS2 mice and USB mice, suddenly the USB mouse worked in the PS2 socket with an adapter.

After the reinstall today - this does not work. I have been trying for 30 minutes now. 

And while typing this reply on another computer, the mouse started working - problems solved (for now anyway).

Beren

---

### Post by Fitch on 2009-11-04
OK, I do know hardware, so I suspect a dodgy plug or cable.  Have you tried a newer ps2 mouse - can you borrow from another computer?

---

