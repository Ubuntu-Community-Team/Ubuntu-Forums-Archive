---
title: "Not your average brightness problem"
date: 2008-04-29
forum: Hardware
---

### Post by Iago1989 on 2008-04-29
I've been trying to get this problem fixed for about 3 days and nobody knows how to fix this. Hopefully you can help me. My brightness won't do anything but be REALLY REALLY dark, and be averagely dim, and I can toggle this by hitting fn+f7. Normally, like on Vista (if you can call that normal) fn+f6 or fn+f5 would toggle my brightness. ALL of my other function keys (volume, media, toggle scr lk, etc.) are working. So it's weird. I know someone else has this problem but aren't being as annoying about it as I am.

What I have already tried:
-gamma control with "displaycalibrator"

-the tutorial "howto" here: [http://ubuntuforums.org/showthread.php?t=767374](http://ubuntuforums.org/showthread.php?t=767374) which is the same as the ubuntu geek method, when I hit fn+up, my music player stops playing, fn down, it pauses/plays. That's how it normally works in Windows, so it probably isn't mapping the brightness over the normal function.

-The "ugly hack" described in [http://ubuntuforums.org/showthread.php?t=767219&highlight=brightness](http://ubuntuforums.org/showthread.php?t=767219&highlight=brightness) 
^ Im not sure why that doesn't work.

-One thing I'd like to try (it seemed bright, but I was in a bright room) was I entered the gecko power management config(I forgot the command! It's something like gkconfig?) So I need to be reminded of that enter-geck-config-command...

-The brightness applet on the panel does nothing.


-I am getting nauseous, I have to strain to read the screen because it's so dark

---

### Post by nawitus on 2008-04-29
Try this in terminal
```

echo 'for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done' > brightness
chmod +x brightness
sudo ./brightness

```

---

### Post by Iago1989 on 2008-04-29
; unexpected

---

### Post by nawitus on 2008-04-29
Try this first:
```

echo 'for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done' > brightness

```

If that doesn't work, create a file using nano (nano brightness in terminal), with a single line:
```

for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done

```
Press control and x to save the file as brightness.

Then the rest as the same:
```

chmod +x brightness
sudo ./brightness

```

---

### Post by Iago1989 on 2008-04-29
when I do the first one normally, I get "access denied" so I prefix it with  "sudo for i..." etc. and it says error near "do"
```
iago@NISUS:~$ echo "for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done" > brightness
iago@NISUS:~$ chmod +x brightness
iago@NISUS:~$ sudo ./brightness
./brightness: 1: Syntax error: ";" unexpected
iago@NISUS:~$ echo "for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done" > brightness
iago@NISUS:~$ chmod +x brightness
iago@NISUS:~$ sudo ./brightn
sudo: ./brightn: command not found
iago@NISUS:~$ echo "for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done" > brightness
iago@NISUS:~$ chmod +x brightness
iago@NISUS:~$ sudo ./brightness
./brightness: 1: Syntax error: ";" unexpected
iago@NISUS:~$ echo "for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done" > brightness
iago@NISUS:~$ chmod +x brightness
iago@NISUS:~$ sudo ./brightness
./brightness: 1: Syntax error: ";" unexpected
iago@NISUS:~$ for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done
bash: /sys/class/backlight/acpi_video0/brightness: Permission denied
bash: /sys/class/backlight/asus-laptop/brightness: Permission denied
iago@NISUS:~$ sudo for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done
bash: syntax error near unexpected token `do'
iago@NISUS:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
iago@NISUS:~$ sudo for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done
bash: syntax error near unexpected token `do'
iago@NISUS:~$ for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done
bash: /sys/class/backlight/acpi_video0/brightness: Permission denied
bash: /sys/class/backlight/asus-laptop/brightness: Permission denied
iago@NISUS:~$ for i in /sys/class/backlight/*/brightness; do echo 10 > $i;
> 
> 
> done
bash: /sys/class/backlight/acpi_video0/brightness: Permission denied
bash: /sys/class/backlight/asus-laptop/brightness: Permission denied
iago@NISUS:~$ sudo for i in /sys/class/backlight/*/brightness; do echo 10 > $i
bash: syntax error near unexpected token `do'
iago@NISUS:~$ sudo for i in /sys/class/backlight/*/brightness
sudo: for: command not found
iago@NISUS:~$ sudo command
sudo: command: command not found
iago@NISUS:~$ sudo chmod +x brightness
iago@NISUS:~$ sudo ./brightness
./brightness: 1: Syntax error: ";" unexpected
iago@NISUS:~$ sudo ./brightness;
./brightness: 1: Syntax error: ";" unexpected
iago@NISUS:~$ echo "for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done" > brightness
iago@NISUS:~$ 
iago@NISUS:~$ 
iago@NISUS:~$ echo "for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done" > brightness
iago@NISUS:~$ chmod +x brightness
iago@NISUS:~$ sudo ./brightness
iago@NISUS:~$ 

```

---

### Post by nawitus on 2008-04-29
See my updated reply, I modified the first command (now it uses ' instead of "). Like this:
```

echo 'for i in /sys/class/backlight/*/brightness; do echo $1 > $i; done;echo Brightness set to $1' > brightness; sudo cp brightness /usr/local/bin/; sudo chmod +x /usr/local/bin/brightness;

```

After that you can use a new command called brightness:
```

nawi ~ $ sudo brightness 0
Brightness set to 0
nawi ~ $ sudo brightness 10
Brightness set to 10

```

---

### Post by Iago1989 on 2008-04-29
iago@NISUS:~$ echo 'for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done' > brightness
iago@NISUS:~$ for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done
bash: /sys/class/backlight/acpi_video0/brightness: Permission denied
bash: /sys/class/backlight/asus-laptop/brightness: Permission denied
iago@NISUS:~$ 
iago@NISUS:~$

---

### Post by nawitus on 2008-04-29
See my last reply, it has 1 single command that even you cannot fail.

---

### Post by Iago1989 on 2008-04-29
I believe this is quite the epic fail then
```
iago@NISUS:~$ echo 'for i in /sys/class/backlight/*/brightness; do echo $1 > $i; done;echo Brightness set to $1' > brightness; sudo cp brightness /usr/local/bin/; sudo chmod +x /usr/local/bin/brightness;
iago@NISUS:~$ nawi ~ $ sudo brightness 0
bash: nawi: command not found
iago@NISUS:~$ nawi ~ $ sudo brightness 10
bash: nawi: command not found
iago@NISUS:~$ Brightness set to 10
bash: Brightness: command not found
iago@NISUS:~$ echo 'for i in /sys/class/backlight/*/brightness; do echo $1 > $i; done;echo Brightness set to $1' > brightness; sudo cp brightness /usr/local/bin/; sudo chmod +x /usr/local/bin/brightness;
iago@NISUS:~$ nawi ~ $ sudo brightness 0
bash: nawi: command not found
iago@NISUS:~$ Brightness set to 0
bash: Brightness: command not found
iago@NISUS:~$ nawi ~ $ sudo brightness 10
bash: nawi: command not found
iago@NISUS:~$ Brightness set to 10
bash: Brightness: command not found
iago@NISUS:~$ 
iago@NISUS:~$ 

```


EDIT: Sorry for failing, I don't really know what I'm doing wrong.

---

### Post by Iago1989 on 2008-04-29
I redid the first one, line by line, and it seemed to work, except my actual brightness didn't change.

```
iago@NISUS:~$ echo 'for i in /sys/class/backlight/*/brightness; do echo 10 > $i; done' > brightness
iago@NISUS:~$ 
iago@NISUS:~$ chmod +x brightness
iago@NISUS:~$ 
iago@NISUS:~$ sudo ./brightness
iago@NISUS:~$ brightness
/usr/local/bin/brightness: line 1: /sys/class/backlight/acpi_video0/brightness: Permission denied
/usr/local/bin/brightness: line 1: /sys/class/backlight/asus-laptop/brightness: Permission denied
Brightness set to
iago@NISUS:~$ sudo brightness
Brightness set to
iago@NISUS:~$ sudo brightness 10
Brightness set to 10
iago@NISUS:~$ sudo brightness 1
Brightness set to 1
iago@NISUS:~$ sudo brightness 1000
Brightness set to 1000
iago@NISUS:~$ 
iago@NISUS:~$ 


```

---

### Post by Iago1989 on 2008-04-29
I guess I annoyed him away. I thanked him anyway. Anybody else willing to give this a go?

---

### Post by Iago1989 on 2008-04-30
Update: I found an application called "monitor settings" but it doesnt work. It gives me the following error: "No monitor supporting DDC/CI available. If your graphics card need it, please check all the required kernel modules are loaded (12c-dev, and your framebuffer driver).

Secondly, one problem with what the previous guy gave me is there is no /sys/class/backlight/brightness, on my laptop it goes /sys/class/backlight/asus-laptop/brightness, there's also /max-brightness, and other tings in asus-laptop. I cant even open it in gedit, though. The little documents in my asus-laptop brightness do change with his commands, but it doesn't effect my brightness.

---

### Post by K_REY_C on 2012-06-29
I'm running Fedora 17 w/ xmonad. The key for me was to run the following to execute the command:

```
sudo ./brightness 2
```

This worked. 

Thanks for the help years later.

---

### Post by mojo risin on 2012-06-29
I don't know the age of your Screen, but there may be the option that your screen is simply failing . Have you tried a different screen on your computer?
(my old screen has been quite dark of late and after that it also had resolution errors, and it turned out that it is just the end of its life.)

---

