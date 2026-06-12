---
title: "Don't turn of external screen on Laptop Lid close event"
date: 2012-06-07
forum: Hardware
---

### Post by Jense on 2012-06-07
Hello,

I have been trying to figure this out for quite some time know and it's driving me crazy.

Problem:
I want to use an external monitor only. The laptop should be stored somewhere with the lid closed. But whatever I try the external screen tuns blank when I close the lid of the laptop.

Setup
Ubuntu 12.04, Nvidia Drivers installed, using xorg.conf settings to have only my external monitor activated on boot.

Tested solutions
[LIST]
[*]Energy-settings -> When lid closed: do nothing
[*]Brightness and Lock Screen: Don't turn of screen and don't block (yes I want it that way)
[*]gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"
[*]edit /etc/acpi/events/lidbtn and comment out line 5 (action line)
[/LIST]

My interpretation of the problem:

As I am using the nvidia driver (and it seems I must as noveau apparently doesn't recognize my external screen) unity is unaware that I actually have an external screen attached. And though via xorg.conf my primary (laptop) screen is disabled unity will no matter what I do disable my screen because it still thinks it is the laptop screen.

Thanks for your help

---

### Post by 4partee on 2012-06-08
I sure hope someone has a solution for this using 10.04.

I am trying to set up a Lenovo notebook as a desktop where I can close the lid on the notebook and put it aside while using an external wireless keyboard and mouse, and an external monitor.

John

---

### Post by Jense on 2012-06-12
Really? Nobody? I can't believe this is not possible. :(

---

### Post by jlmjlm on 2012-06-13
So far, it is working for me to replace the /etc/acpi/lid.sh file with:
```
case $(awk '{ print $2 }' <  /proc/acpi/button/lid/LID0/state) in
         open) vbetool dpms on;;
         close) vbetool dpms off;;
esac
```Then when I close the lid the backlight goes out and nothing else happens, and when I open it the backlight comes back on.
It's annoying that the default behavior is to blank external monitors when a laptop's lid is closed, and even more annoying that the "do nothing" settings aren't honored.

---

### Post by Jense on 2012-06-14
Hi,

thanks for your advice. I will try that as soon as I get home.

---

### Post by Randy M on 2012-06-16
> **jlmjlm said:**
> So far, it is working for me to replace the /etc/acpi/lid.sh file with:
```
case $(awk '{ print $2 }' <  /proc/acpi/button/lid/LID0/state) in
         open) vbetool dpms on;;
         close) vbetool dpms off;;
esac
```Then when I close the lid the backlight goes out and nothing else happens, and when I open it the backlight comes back on.
It's annoying that the default behavior is to blank external monitors when a laptop's lid is closed, and even more annoying that the "do nothing" settings aren't honored.

I tried this on my HP G60 and it didn't work. I'm running 10.04 there. The backlight it burned out and I want to use it with a monitor. Any other suggestions? Thanks in advance.

---

### Post by Randy M on 2012-06-16
I think I found it. 
 
If there's no "Do Nothing" option in the Power Settings, open a terminal and enter "gconf-editor". The select "apps", "gnome-power-manager", and "buttons". Then, set "lid_ac" and "lid_battery" to "nothing" (right click, select "Edit" and type in "nothing" without the quotes) and reboot.

---

### Post by thomhehl on 2012-06-17
> **Jense said:**
> Hello,

I have been trying to figure this out for quite some time know and it's driving me crazy.

Problem:
I want to use an external monitor only. The laptop should be stored somewhere with the lid closed. But whatever I try the external screen tuns blank when I close the lid of the laptop.

Setup
Ubuntu 12.04, Nvidia Drivers installed, using xorg.conf settings to have only my external monitor activated on boot.

Tested solutions
[LIST]
[*]Energy-settings -> When lid closed: do nothing
[*]Brightness and Lock Screen: Don't turn of screen and don't block (yes I want it that way)
[*]gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"
[*]edit /etc/acpi/events/lidbtn and comment out line 5 (action line)
[/LIST]

My interpretation of the problem:

As I am using the nvidia driver (and it seems I must as noveau apparently doesn't recognize my external screen) unity is unaware that I actually have an external screen attached. And though via xorg.conf my primary (laptop) screen is disabled unity will no matter what I do disable my screen because it still thinks it is the laptop screen.

Thanks for your help
I am having the same issue on 12.04 on my Acer Aspire laptop. Did you ever find a resolution?:confused:

---

### Post by Jense on 2012-06-20
> **jlmjlm said:**
> So far, it is working for me to replace the /etc/acpi/lid.sh file with:
```
case $(awk '{ print $2 }' <  /proc/acpi/button/lid/LID0/state) in
         open) vbetool dpms on;;
         close) vbetool dpms off;;
esac
```

As this will also disable the backlight of the external screen this workaround doesn't work for me (tried it). I have not yet found any other solution. I am wondering... this isn't such an unusual use case. Why is this so difficult? Maybe it's just unity...

---

### Post by Jense on 2012-06-21
I filed a bug report here:

[https://bugs.launchpad.net/ubuntu/+bug/1015796](https://bugs.launchpad.net/ubuntu/+bug/1015796)

If you are also interested in getting this fixed, give it some heat :-)

---

