---
title: "Acer 4810tz screen brigtness no longer fixable after kernel update (regression)"
date: 2009-09-28
forum: Hardware
---

### Post by wilcoxjay on 2009-09-28
Hello all,

I'm running karmic on an Acer Timeline 4810tz, and until very recently, everything was fine. Yesterday, I ran update-manager, and restarted, to find that my trackpad was no longer working at all. Doing some research, I found that people had success by updating to a more recent (development) kernel. I installed 2.6.31-020631-generic from the PPA-mainline, and restarted, and the trackpad worked.

Now, adjusting the screen brightness doesn't work out of the box on my timeline, so I've been using the fix 
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```and then adjusting with
```
xbacklight -set 10
``` or whatever percentage. 

After the kernel update, the xrandr command gives the following error. 
```
james@ubuntu:~$ xrandr --output LVDS --set BACKLIGHT_CONTROL native
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30

```Somewhere I read that someone else had this same error, but they had never had it working in the first place. I think this is relevant:
```
james@ubuntu:~$ xrandr --prop
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
    EDID_DATA:
        00ffffffffffff0006af3c2100000000
        01120103801f11780a09e59757549327
        22505400000001010101010101010101
        010101010101201c5680500023303020
        360035ae100000180000000f00000000
        00000000000000000020000000fe0041
        554f0a202020202020202020000000fe
        004231343058573032205631200a00b2
    scaling mode:    Fullscreen
        supported: Non-GPU      Fullscreen   No scale     Aspect      
   1366x768       60.0*+
   1360x768       59.8  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```And as you can see, there is no ```
BACKLIGHT_CONTROL
``` line, so I'm very confused.

Can anyone offer suggestions on how to fix this?

If you need more info/log files, please let me know.

Thanks in advance,

James

EDIT: Also could someone tell me if it's appropriate to file this as a bug on Lanchpad, and if so, under what package? Thanks.

---

### Post by Sashin on 2009-09-28
I have this problem too on Karmic.

---

### Post by wilcoxjay on 2009-09-28
> **Sashin said:**
> I have this problem too on Karmic.

Just to be clear, is your problem caused (or does it appear to be caused) by a kernel update (specifically to 2.6.31-020631)? What's your output of [FONT=Courier New]uname -r[/FONT]? 

James

---

### Post by dwinks on 2009-09-29
I have this issue as well.  uname -r has the output of 2.6.31-11-generic since I have my system currently fully updated.

---

