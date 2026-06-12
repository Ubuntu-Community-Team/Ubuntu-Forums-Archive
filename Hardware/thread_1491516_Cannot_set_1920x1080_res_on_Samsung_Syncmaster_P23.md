---
title: "Cannot set 1920x1080 res on Samsung Syncmaster P2370"
date: 2010-05-23
forum: Hardware
---

### Post by AxlDLuffy on 2010-05-23
Hello everyone, I have a Samsung Syncmaster P2370 with a native resolution of 1920x1080@60. The thing is that in Ubuntu (and every other distro I tried) I cannot set the monitor in 1920x1080. In Windows in order to achieve 1920x1080 I have to install the monitor "driver" which obviously adds the modelines. But Samsung does not have Linux support. 

I have tried dozens of mods to the xorg.conf in order to achieve the desired resolution but with no luck. A fellow UbuntuForums Member suggested I find someone with the same monitor with me who has succeeded in achieving 1920x1080 in order to give me his EDID in binary. 

So, has anyone a **SAMSUNG SyncMaster P2370**?

Also, can anyone help me in making my own EDID using tools such as Monitor Asset Manager or Pheonix EDID Designer, cause my monitor knowledge is too limited to achieve that.

Thank you in advance!

---

### Post by bahrt on 2010-08-19
Hi,
Don't know if you already resolved this, but I have a P2370 and Ubuntu 10.4 didn't give me any kind of troubles setting resolution to 1920x1080@60, even when it's not detected as such. It seems there was some progress with this since you posted your question.

BTW, if you or anyone else could make Compiz start with this monitor, please share how, because it doesn't seem to work. Maybe the driver is missing (most probably, as Compiz does not detect it and neither does the Preferences -> Monitors -> Detect Monitors button)

---

### Post by sameekhan on 2011-01-16
Hello
I have Samsung Syncmaster 2233 with 1920x1080 res. I installed ubuntu 10.10 but the highest res it is showing is: 1152x864. I searched for the samsung drivers for ubuntu but i did not find anywhere. Can any one help me set the resolution? Thanks in advance :)

---

### Post by Aventinus on 2011-01-16
Hello sameekhan, I had the same issue and fortunately I solved it a long time ago. What I did is to add my modeline using the xrandr command.

Type:

```
$ xrandr
```

You will see all your available resolutions. Now you go [here]("http://www.mythtv.org/wiki/Modeline_Database"). You will have to find the correct modeline for your monitor. For instance mine is: *148.35 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync*
Then type:

```
$ xrandr --newmode "1920x1080_60.00" 148.35 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync

$ xrandr --addmode CRT2 1920x1080_60.00

$ sudo nano /etc/gdm/PreSession/Default
```

and add the following lines:

```
xrandr --newmode "1920x1080_60.00" 148.35 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
xrandr --addmode CRT2 1920x1080_60.00
```

Change the above modeline with the appropriate one. Also change the word CRT2 with your output.

Works on every distro!

---

### Post by mailtodtm on 2011-02-18
I have a Samsung 2494LW and I'm having the same problem. Also, I don't see a modeline for this model as described above. Can anyone help???

Thanks - David

Ubuntu 10.04...

---

### Post by fabio.montefuscolo on 2011-03-13
How can I discover the correct values for modline? I tried the cvt command, but when I run xrandr over cvt results I get a poor quality image, with blurred letter and strange shadows. The values you provided works better than the provided by cvt, but I think that exists better values for my device.

I have a Samsung SyncMaster FX2490HD and Ubuntu 10.10. Before read your post, I tried this:
```

cvt 1920 1080 60
xrandr --newmode "1920x1080_60.00" 173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output VGA1 --mode 1920x1080_60.00

```

Thanks!!

---

### Post by iffy50 on 2011-03-17
> **mailtodtm said:**
> I have a Samsung 2494LW and I'm having the same problem. Also, I don't see a modeline for this model as described above. Can anyone help???

Thanks - David

Ubuntu 10.04...

Hi David,
Did you ever find this info. I got a new 2949lw yesterday and I'm looking for exactly the same info.

---

### Post by fredrik hansson on 2011-08-16
> **fabio.montefuscolo said:**
> 
...
I have a Samsung SyncMaster FX2490HD and Ubuntu 10.10. Before read your post, I tried this:
```

cvt 1920 1080 60
xrandr --newmode "1920x1080_60.00" 173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output VGA1 --mode 1920x1080_60.00

```

Thanks!!

I have the same problem. My screen is Samsung SyncMaster214T. My desired resolution is 1600x1200.
I used xrander to change the resolution (thanks for the tip fabio.montefuscolo).

When I used the modline from this command:
```

cvt 1600 1200 60

```
I had som serious grafic problems. I tried higher reslolutions, and that worked fine. (except that my desktop was now to big for my screen). I tried with smaller resolutions until I found I just had to add one pixel on the Y-resolution.

Now I use the  modline from this command:
```

cvt 1600 1201 60

```
There is probably a row of pixels that I cannot see. But I can live with that. ;)

---

### Post by lacis_alfredo on 2011-08-17
Solved: Hi, I thought would report how I fixed mine - someone tried to make xrandr too smart and it can't cope.  xrandr reported```
# xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
root@Cypress-Creek:/etc

```Which is just stooopid.  My monitor happily does 1600x1200 at 75 Hz.

Now there are **[COLOR="Red"]unlisted[/COLOR]** arguments which can help.  They are not listed when you run xrandr --help, but **[COLOR="Red"]are[/COLOR]** listed in the '[COLOR="Red"]**man**[/COLOR]' page.

They are ```
--q1   Forces the usage of the RandR version 1.1 protocol, even if a higher ver&#8208;
       sion is available.

--q12  Forces  the  usage of the RandR version 1.2 protocol, even if the display
       does not report it as supported or a higher version is available.
```So, long story short, I just ran this: (new resolutions shown in [COLOR="Red"]red[/COLOR]):```
# xrandr **[COLOR="Red"]--q1[/COLOR]** -s 1600x1200 -r 75 
 SZ:    Pixels          Physical       Refresh[COLOR="Red"]
 0   1600 x 1200   ( 370mm x 280mm )   75   60  
 1   1280 x 1024   ( 370mm x 280mm )   85   75  
 2   1280 x 960    ( 370mm x 280mm )   85  
 3   1152 x 864    ( 370mm x 280mm )   75  [/COLOR]
*4   1024 x 768    ( 370mm x 280mm )  [COLOR="Red"] 85   75   70[/COLOR]  *60  [COLOR="Red"] 43 [/COLOR] 
[COLOR="Red"] 5    832 x 624    ( 370mm x 280mm )   75 [/COLOR] 
 6    800 x 600    ( 370mm x 280mm )  [COLOR="Red"] 85   72   75 [/COLOR]  60   56  
 7    640 x 480    ( 370mm x 280mm )  [COLOR="Red"] 85   73   75   67 [/COLOR]  60  
[COLOR="Red"] 8    720 x 400    ( 370mm x 280mm )   88   70 [/COLOR] 
root@Cypress-Creek:/etc
#
```

---

### Post by lacis_alfredo on 2011-08-17
P.S.: I just added a call to xrandr to the front of the script file [FONT="Courier New"][COLOR="Red"]/etc/xdg/lxsession/Lubuntu/autostart[/COLOR][/FONT] :

```

[COLOR="Red"]@xrandr --q1 -s 1600x1200 -r 75[/COLOR]
@nm-applet
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@gnome-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

```

---

