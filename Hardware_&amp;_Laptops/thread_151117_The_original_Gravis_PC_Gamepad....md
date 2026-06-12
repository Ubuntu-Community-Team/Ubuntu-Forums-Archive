---
title: "The original Gravis PC Gamepad..."
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by markiss on 2006-03-27
Well after several hours of reading and trying (experimenting) options with various files, I have a way to get my old Gravis Gamepad to work. The only problem is sound does not work. So as it stands right now either sound or gamepad, not both. Here is what I did, and I obtained most of this from other threads, particularly this one: 

[http://www.ubuntuforums.org/showthread.php?t=55173&highlight=joystick](http://www.ubuntuforums.org/showthread.php?t=55173&highlight=joystick)

Here are my specs. I have an MX34 AcerOpen Motherboard. It has onboard sound integration using the driver snd-via82xx. 

1-It is important to note that I had to enable the gameport in my bios. 
2-After editing the joystick file per the above instructions, I added two lines, **modprobe ns558**, and **modprobe grip**. Aparently these two modules are needed for the Gravis Gamepad.
3-Then I edited the **/ect/modprobe.d/alsa-base** file. (I discovered that it is much easier with my Ubuntu system to right click a file if I want to edit it. Instead of opening **/ect/modprobe.d/alsa-base** in a terminal with nano, I right click and choose scripts and run as root in gedit. Nano just confused me and I ended up fouling up the sound driver. In gedit I edited the file to include the line,  **options snd-via82xx joystick_port=1**  at the end of the file. 

I am able to repeat the results and enable disable the option by adding or removing the $ symbol before the line. With [B]jscalibrator
[/B] my gamepad is recognized. But as I said earlier I have no sound. On boot up it says that my sound card is not recognized. But in **lspci** and **lsmod** both the card and the modules are loaded. I suspect that it is a conflict with the midi drivers. In the circuitry of the onboard sound gameport are two pins that allow out put of midi. Is there a way to rewrite the sound driver to disable midi support? Or is it simpler to just add or erase lines from the config files.

Thanks for all the support and threads so far. This is my first real attempt at understanding Linux and I am so pleased at the versatility of Ubuntu. 

Markiss

---

