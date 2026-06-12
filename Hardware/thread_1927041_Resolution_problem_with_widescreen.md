---
title: "Resolution problem with widescreen"
date: 2012-02-17
forum: Hardware
---

### Post by hriceto on 2012-02-17
Hello all,

I am an inexperienced linux user and wanted to ask if someone could help me with my screen resolution.

I have a dual boot install of ubuntu 10.04 with windows 7. My computer is i7 core with Intel HD graphics 2000.

In ubuntu my screen resolution is 1600x1200 (4:3)
However I have a widescreen and want something like 1920x1080 or anything that is 16:9. xrandr and the GUI monitor app only have 4:3 options and my screen is detected as unknown.

I tried adding a 16:9 resolution through xrandr --newmode but I got an error message saying it cannot set to the resolution.

Any help is appreciated.

---

### Post by bijoalex on 2012-08-04
I know this is a very old post. However, as similar problems still exist, thought this solution will help someone who would be looking for it.

I had similar problem with Ubuntu 12.04 LTS (Precise Pangolin) when running as a VMWare instance from a Windows 7 laptop having resolution 1920x1080. Ubuntu was unable to detect 1920x1080 resolution, though it was able to detect another 16:9 resolution, which is 1360x768.

After playing around a while with xrandr, I figured that the current output I use is "Virtual1". This could be found by running the command

```
xrandr --current
```which gave me the output

```
Screen 0: minimum 1 x 1, current 1680 x 1050, maximum 8192 x 8192
**Virtual1** connected 1680x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
```A list of detected displays followed the above output, which did not have 1920x1080.

This told me that I have to create a new mode "1920x1080" and add it to the Virtual1 output by running the xrandr command with below syntax

```
xrandr --newmode _name_ _mode_
```However, I had no clue on what details to provide in mode argument. The command cvt came to my rescue there, which calculates those details based on the width and height of the resolution you plan to use.

```
cvt -v 1920 1080 60
```The last option 60 in there is the optional refresh rate. This command gave me below output.

```
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline **"1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync**
```I ignored the trailing "_60.00" in the mode name when I used it with xrandr.

Now I have all the details I need to run the xrandr and get this going.

```
xrandr --newmode "1920x1080" 173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode Virtual1 1920x1080
xrandr --output Virtual1 --mode 1920x1080
```Voila, my screen is now with the 1920x1080 resolution.

What I need to see now is if this resolution remains there even after I restart the host. Will post an update in this thread later on that.

---

### Post by bijoalex on 2012-08-04
As I was afraid, once host was restarted, the screen resolution went back to the original lower resolution instead of 1920x1080.

So I added the last three commands (given below again) to the file ~/.xprofile

```
xrandr --newmode "1920x1080" 173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode Virtual1 1920x1080
xrandr --output Virtual1 --mode 1920x1080
```

Restarted the host again. Resolution was still lower.

Opened System Settings > Displays. 1920x1080 was there in the list of resolutions. Selected that and clicked Apply.

Restarted the host and now the resolution is permanent at 1920x1080. However, the resolution is at 1920x1080 only after I login. Until then, it's lower resolution.

---

### Post by bijoalex on 2012-08-05
Fixed the splash resolution with help from this link
[http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen](http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen)

Bringing the key content from there for easy reference
> That is easy. First of all:
  ```
sudo apt-get install v86d hwinfo sudo hwinfo --framebuffer
```   This will show you your supported resolutions. **Take note**.
I took note of
```
Mode 0x0367: 1920x1080 (+7680), 24 bits
```> **Then:**
  ```
gksu gedit /etc/default/grub
```   Search for - GRUB_GFXMODE=
  below this you need to type:
```
GRUB_GFXPAYLOAD_LINUX=1920x1080
```  Save the file and then:
  ```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-grub2
sudo update-initramfs -u
```Restart the host.

---

### Post by hriceto on 2012-09-16
bijoalex,

I was going to try your sugestion but before I did it I upgraded to 12.04 LTS and after a restart my screen was detected correctly. 
Now I have 1920x1080 and the splash screen is working too without doing any work. 
Thanks for the help though.

---

