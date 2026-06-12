---
title: "Brightness not working in Sony Vaio VGN SR129EB, with Radeon HD 3470 graphic card"
date: 2008-09-10
forum: Hardware
---

### Post by a3qp on 2008-09-10
Hi,

After a couple of days having left the dual booting and installing just ubuntu, I started to notice that my screen was pretty "gray" or dark, and what used to be white (as this background color) looks much darker than before. I remember that in windows the colors were very intense, but now I can't check.

I have a Sony Vaio VGN SR 129 E/B, and a Radeon HD 3470 graphic card.

I have tried:
a) Use fn keys, but they are not working (just volume keys work)
b) Run Ubuntu through Live CD. The brightness is the same, and the brightness fn keys don't work either.
c) Check BIOS. I have just 4 menus (main, security, boot and exit) and no option to control brightness or screen or anything close to that.
d) I installed xbacklight. When I tried it, I got: "No outputs have backlight property"
e) Then I tried xrandr:
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```
But I got:
```
a3qp@a3qp-laptop:~$ xrandr --output LVDS --set BACKLIGHT_CONTROL native
X Error of failed request:  173
  Major opcode of failed request:  159 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  14
  Current serial number in output stream:  14

```
f) Finally, I tried to set acpi=off: In terminal I wrote:

sudo gedit /boot/grub/menu.lst

Then I add the "acpi=off" option to the end of the "kernel" line as below:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5725877-5158-4c5f-b858-e0f6eededc1e ro quiet splash **acpi=off**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

But I got no change. And the fn brightness keys still don't work.

Any suggestion would be appreciated.

Thanks

---

### Post by pytheas22 on 2008-09-12
If you have special keys or buttons on your computer to turn on and off the wireless card, volume, etc., do they work?  Or do you use the function keys to do all of that?

---

### Post by a3qp on 2008-09-13
Hi Pytheas22, 

The wireless connection is controlled by a built-in switch, which is in the front od the PC. The volume is controlled with fn+F2, fn+F3 and fn+F4 (which are mute, increase volume and decrease volume respectively).

The other fn keys are:
 
fn+F5 and fn+F6 which are increase and decrease of brightness
fn+F7 which is to let monitor signal to go to a projector.
fn+F9 and fn+F10 which is zoom in and out.
and some other less frequently used.

It only works the fn volume keys. All the rest is not working at all.

---

### Post by pytheas22 on 2008-09-13
I googled around and it seems that there are a lot of issues with the function keys, on Sony laptops in particular.  I found two things that you might want to try.  First, there's a script [here]("http://intentionallyobsolete.com/?p=23") that says it will automatically fix the problem.  To run it, type:
```

wget http://www.intentionallyobsolete.com/projects/feisty-fsfn.sh
sudo feisty-fsfn.sh
```

It's for Feisty, but maybe it will work on Hardy too.

If that doesn't help, take a look at [this page]("http://users.skynet.be/thomasvst/linux-on-laptop/#Hotkeys"); those instructions may do the trick.  Let us know if you have success.

---

### Post by a3qp on 2008-09-13
Thanks for the solutions. Unfortunately, I have no good news.

I did the first method:

```
wget http://www.intentionallyobsolete.com/projects/feisty-fsfn.sh
sudo feisty-fsfn.sh
```

but i got a command not found error, although I was in the same directory:

```

a3qp@a3qp-laptop:~$ sudo feisty-fsfn.sh
sudo: feisty-fsfn.sh: command not found
a3qp@a3qp-laptop:~$ ls
Desktop  disco1  disco2  feisty-fsfn.sh  PDF

```


Then I tried the second potential solution, which is [here]("http://users.skynet.be/thomasvst/linux-on-laptop/#Hotkeys") 
Let me rewrite it:
```

wget http://users.skynet.be/thomasvst/linux-on-laptop/download/sony_acpi.tar.gz
tar xzvf sony_acpi.tar.gz
cd sony_acpi
make
sudo cp sony_acpi.ko /lib/modules/`uname -r`/kernel/drivers/acpi/
sudo gedit /etc/modules

```
Add the line sony_acpi at the end of the file
Then
```

wget http://users.skynet.be/thomasvst/linux-on-laptop/download/sonyfn.c
gcc sonyfn.c -o sonyfn
sudo mv sonyfn /usr/sbin
sudo gedit /etc/init.d/bootmisc.sh

```
Add the line 
[B]
sonyfn & 
[/B]
after the line : [ -f /etc/default/rcS ] && . /etc/default/rcS (at approximatively line 10).

Then save and reboot.

However, everything worked fine, until the last line, where I didn't find the line: [ -f /etc/default/rcS ] && . /etc/default/rcS

I have:

### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin
[ "$DELAYLOGIN" ] || DELAYLOGIN=yes
sonyfn &
. /lib/init/vars.sh

do_start () {
	#
...

So I put the line **sonyfn & ** right after the line:
**[ "$DELAYLOGIN" ] || DELAYLOGIN=yes**

Should I place it in other part?

Thanks

---

### Post by pytheas22 on 2008-09-13
Sorry, try running the first script again...I forgot that the file probably wouldn't be executable.  Run this and it should work:
```

wget http://www.intentionallyobsolete.com/projects/feisty-fsfn.sh
sudo chmod +x feisty-fsfn.sh
sudo sh feisty-fsfn.sh
```

---

