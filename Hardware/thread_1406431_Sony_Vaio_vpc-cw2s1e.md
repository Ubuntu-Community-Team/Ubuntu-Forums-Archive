---
title: "Sony Vaio vpc-cw2s1e"
date: 2010-02-14
forum: Hardware
---

### Post by steffenomak on 2010-02-14
Just bought the computer and it came with windows 7, but i wanted to have ubuntu on it so i formated the recovery partition. But the problem is that i have several problems whit ubuntu. The problems are

- Wifi, slow as hell. It finds my network at home but is slower then in windows 7 when it comes to transfere.

- Video drivers. After installing them using hardware drivers from administration and after reboot the screen is just black. I can boot in to recovery but then i only have a terminal and when i run the command startx i just get a black screen.

- Screen brightness. I cant change it at all. I whant to be able to change it but when i try fn+f3/f4 to change screen brightness nothing happans.

the specs:
Core i3, i3-330M 2,13GHz, 2.5 GT/s, 3MB
GeForce GT 330M 512MB

more then that i dont know so.

Thanks for the help

---

### Post by steffenomak on 2010-02-15
so nobudy has an idea to what i should do?

---

### Post by ChTiMi on 2010-02-15
I bought the same laptop last week... and I got these problems too...

If you want to use lastest nvidia drivers, you have to :
- Put attached file into /etc/X11/
- Replace "Device" section in your /etc/X11/xorg.conf :

```

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    Option "ConnectedMonitor"   "DFP-0,CRT-0"
    Option "CustomEDID"         "DFP-0:/etc/X11/sony-edid.bin"
EndSection

```

For wireless speed, install :
- linux-backports-modules-karmic
- linux-backports-modules-karmic-generic
- wicd (this will remove network-manager)

Sorry for my english...

---

### Post by steffenomak on 2010-02-15
> **ChTiMi said:**
> I bought the same laptop last week... and I got these problems too...

If you want to use lastest nvidia drivers, you have to :
- Put attached file into /etc/X11/
- Replace "Device" section in your /etc/X11/xorg.conf :

```

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    Option "ConnectedMonitor"   "DFP-0,CRT-0"
    Option "CustomEDID"         "DFP-0:/etc/X11/sony-edid.bin"
EndSection

```

For wireless speed, install :
- linux-backports-modules-karmic
- linux-backports-modules-karmic-generic
- wicd (this will remove network-manager)

Sorry for my english...

thanks for the reply gonna test it in a little bit but thanks again. I like to develop in ubuntu and stuff.

EDIT:
Now everything works exceps screen brightness

---

### Post by devottam on 2010-03-01
i had got the same problems...
managed to solve (like the one described above) the graphics problem (3d graphics rocks)....
however you have to pay the price....can't use the terminals  :-(
for the brightness i couldn't solve it [there are plenty of workouts but they doesn't solve the problem with vaio CW series
hope somebody just figures out ....my eyes are burning out :-(

---

### Post by ChTiMi on 2010-03-02
in order to adjust brightness you can go to : system -> administration -> nvidia x settings -> x server color correction

i'm waiting for new nvidia's driver (early march). It will include support for 300m series... to be continued

---

### Post by steffenomak on 2010-05-10
> **ChTiMi said:**
> in order to adjust brightness you can go to : system -> administration -> nvidia x settings -> x server color correction

i'm waiting for new nvidia's driver (early march). It will include support for 300m series... to be continued

Thats the color correction and not the light, that consumes lots of power from the battery

---

### Post by Bahr on 2010-10-02
I have the same problem using Ubuntu 10.04 with my Vaio CW2S1E. 

If this is solved, where is the solution:confused:

I can't use Ubuntu right now, because it is completely unusable because of the brightness setting, and the Gnome brightness applet does not work, and adjusting the color is not a solution either. 

So has anybody figured this out?

---

### Post by steffenomak on 2010-10-02
> **Bahr said:**
> I have the same problem using Ubuntu 10.04 with my Vaio CW2S1E. 

If this is solved, where is the solution:confused:

I can't use Ubuntu right now, because it is completely unusable because of the brightness setting, and the Gnome brightness applet does not work, and adjusting the color is not a solution either. 

So has anybody figured this out?

It isn't fully solved but you can use linux. The screen brightness and bad wireless are the only two stuff that are a problem.

---

### Post by bthoward on 2010-10-23
The wireless is only a temporary problem that is stemming from the intel iwlagn driver.  Give it a little time and the team will push new drivers out and your speeds will be on par with Windoze at a minimum.  Usually Linux tends to have less network overhead and will provide slightly better speeds.

---

