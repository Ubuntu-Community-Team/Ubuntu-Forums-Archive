---
title: "Samsung 900X4C, keyboard backlit command in boot"
date: 2012-10-10
forum: Hardware
---

### Post by marcoperez on 2012-10-10
Hi,
I have a new samsung 900X4C and have installed ubuntu as single OS (12.0.4 LTS and today I have upgraded the kernel to 3.4.1-030401-generic).
I'm very happy with the computer and everything works ok, except some Fn keys like Fn+F9/F10 (keyboard backlit) and F12 (wireless is always on - I can turn on/off only with command line) and F11 (the same problem).
Today I've upgraded the kernel to 3.4.1-030401-generic and so I've solved the problem of keyboard backlit. Now, with this kernel, I can turn on/off the keyboard backlit with the command
sudo echo 4 > /sys/devices/platform/samsung/leds/samsung::kbd_backlight/brightness
The values can be between 1 and 8.

Note: it's not enough sudo... to work I have to put su before

[B][I]mp@mp-900X4C:~$ sudo echo 4 > /sys/devices/platform/samsung/leds/samsung::kbd_backlight/brightness
bash:/sys/devices/platform/samsung/leds/samsung::kbd_backlight/brightness: Permissão negada
mp@mp-900X4C:~$ su
Senha: 
root@mp-900X4C:/home/mp# sudo echo 4 > /sys/devices/platform/samsung/leds/samsung::kbd_backlight/brightness
root@mp-900X4C:/home/mp#[/FONT][/I][/B][/COLOR]
(and it works)

Why do not work with sudo? It's not the same thing??

Then I have tried to execute the command in boot. I try to solve this in two possible ways:

1)
I have put the command in rc.local (/etc/rc.local or /etc/init.d/rc.local).

...
echo 4 | sudo tee /sys/devices/platform/samsung/leds/samsung::kbd_backlight/brightness
echo 0

or

...
sudo echo 4 > /sys/devices/platform/samsung/leds/samsung::kbd_backlight/brightness
echo 0

I have changed the permisions obviously
sudo chmod +x <file_name>

and none works!!!! It seems that the file is ignored in boot

2) 
I have created the script
/etc/init.d/keyboard-backlit.sh

with

echo 4 | sudo tee /sys/devices/platform/samsung/leds/samsung::kbd_backlight/brightness

and then I have created a symbolic link in /etc/rc2.d/S99keyboard-backlit.sh --> /etc/init.d/keyboard-backlit.sh

and then again in reboot doesn't work:((((


it seems the a simple problem but I can not do it work...

Can you help me please...

---

### Post by oldos2er on 2012-10-10
Post moved to its own thread.

---

