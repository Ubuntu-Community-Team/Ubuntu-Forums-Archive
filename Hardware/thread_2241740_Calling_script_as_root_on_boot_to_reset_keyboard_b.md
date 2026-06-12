---
title: "Calling script as root on boot to reset keyboard backlight"
date: 2014-08-28
forum: Hardware
---

### Post by sikh4life on 2014-08-28
Hello All,

I have tried everything I can and cant figure this out so im asking for help. I would like to basically set my keyboard backlight to 0 after the x session has started. Basically when the computer boots, backlight on keyboard is off until the xsession starts. Once the x session starts and I have a login screen, BAM FULL BRIGHTNESS on the backlight. I found the file im suppose to "echo 0" to. I put the one liner in rc.local and it didnt run. The one liner to set my screen brightness to a custom value and not full brightness works when in rc.local. But, I can put the keyboard backlight one liner under it and it doesnt work. I can put it above it, and it quits the script because then my full screen brightness one liner doesnt work.

I figured this might have something to do with X because rc.local runs before X does. So everything is fine until X is init/started and then the file with the brightness value gets modified. This is what I assume because I can get the screen brightness to set on boot everytime with rc.local but not the backlight for the keyboard.

Ive tried calling a script with the code for the keyboard backlight reset and that didnt work. I then had the script get called, and enter sleep for a minute before it ran the command incase the X session didnt start when the script was ran, that didnt work either. I tried value's all the way up to 5 and nothing worked.

So, thats what ive done and would appreciate any help. The one liner is 
```

# set keyboard backlight so its not at max on boot
echo 0 > /sys/class/leds/smc::kbd_backlight/brightness

```

I should add that both commands need to be run by root. So thats why I thought rc.local would be good. If I do .gnomrc or .bash_login like ive been reading, it wont work becuase it would run as me. If I sudo it, it would ask for a password. I could echo a password and pipe it to sudo, or add myself to the sudoers but neither is secure or ideal. What I would like to do is find a "rc.local" way of launching this script as root without user interaction and have my little "patches" work. The screen one works fine, I have one for keyboard backlight and a few others that I would like to run on start up since they cant be made persistent.

If you have any additional questions or need logs please ask. I dont know what log to look at to see what line/command failed when rc.local was called or I would look there. Heres hoping someone else knows how to fix my problem.

Thanks,
Sikh

---

