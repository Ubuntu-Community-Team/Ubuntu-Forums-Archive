---
title: "kernel panic when agp enabled"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by munim on 2006-02-06
Hi.
ever since i installed a nvidia 6200 agp from bigtek on my asrock intel chipset 865gv motherboard, i just can't boot linux.. and this doesn't apply to ubuntu.. i tried many distributions.
i am not exactly a newbie in linux.. but i just can't manage to rectify the problem.
it only seems to happen with the AGP display card is enabled from the BIOS.. when my onboard card is enabled everything runs fine... but i have to keep changing my monitor cable to the right display adapter.
When i try to start Ubuntu in normal mode.. it gets stuck in "Starting Hotplug System".
When i choose the recovery option, it shows this:
error_code +0x4f/0x54
Fatal exception in interrupt
Kernel panic: Not syncing
I get varied versions of this kernel panic message for different distributions.
I tried noprobe and noirqdebug.. it didn't help.
I downloaded and installed the latest version of the BIOS from my motherboard company's website.
I also installed and downloaded the latest nvidia drivers (in another distro.. not for ubuntu.. cuz it doesn't seem to help)
Infact I posted this question in the NVIDIA support forum and they weren't able to help me... so I came here.
HELP!

---

### Post by munim on 2006-02-06
oh i forgot.. i use ubuntu 5.10

---

### Post by munim on 2006-02-07
oh common.. don't tell me that no one can help me in this problem!
and it just takes one day for this post to move to the second page?!:evil: 
guys please i need help badly.. i just can't get linux to work..

---

### Post by LordBug on 2006-02-07
> it only seems to happen with the AGP display card is enabled from the BIOS.. when my onboard card is enabled everything runs fine... 

Sounds like you need to disable the onboard in BIOS so only the nVidia card is left.

---

### Post by munim on 2006-02-07
[QUOTE=LordBug]Sounds like you need to disable the onboard in BIOS so only the nVidia card is left.[/QUOTE]
there is an option in my bios setting where i can set the graphics priority..
they are:
agi/pci/onboard
pci/agi/onboard
onboard/pci/agi

if i select any of the first two my agp card works and linux crashes as explained in first post.(i don't have a PCI graphics card)
if i select the third my onboard card is enabled and linux works.... but i want it work to with my agp card, else i have to keep changing the settings and change the cable location to switch to linux.
also if the third option is enabled i get another option which shows the amount of mem i can set for onboard card:
Options are:
Auto
Enabled, 2mb
...
..
..
Enabled, 32mb

Whatever I select my onboard card only starts up.. and there is no option anywhere in the BIOS to disable my onboard card.. only the option to change the priority of graphics cards as described above.
I have onboard LAN, sound and the BIOS also shows an onboard modem option.. i can set these to auto or disabled.. but they don't work.
nothing seems to get linux to work with my graphics card enabled on my bios.

This isn't a standard problem... i heard it has something to do with my asrock i895gv motherboard working with agp on linux... i tried the asrock website but i couldn't find anything.

---

### Post by Stormbringer on 2006-02-07
Hi, munim!

There's no such thing as a "i895gv" on the ASRock website.

Could you please be a little more specific and give the model of your mainboard so that one can take a look into the manual? Maybe this will lead one step further in getting a solution to your problem...

Storm.

---

### Post by munim on 2006-02-07
sorry Stormbringer i meant asrock intel chipset 865gv... as mentioned in the first post.
anyways i got the solutions myself (thanks a lot for helping u guys:mad: )
anyways just for the record and for other who might have the same problem.. here is the solution..
1. Boot with linux with your onboard card cuz it will boot that ways and you have to boot to change a file's permission
2. The X-Server won't start as you have booted with a different graphics card and ask will you if you want the diagnose the problem. Select No. In some distributions it will start with after displaying an error and detecting the onboard graphics card.. in this case login with root and open the terminal (its there in the accessories menu)
3. Login. Use the root account.
4. type this: chmod -x /etc/init.d/hotplug
5. If you have went to the NVIDIA forums, you may have already done the following steps.. if you haven't... type "vi /etc/X11/xorg.conf"
6. Find the part where it shows something like this:
Section "Device"
Identifier "your onboard graphics card.. whatever..."
Make these changes(press INSERT first):
Section "Device"
Identifier "Videocard 0"
Driver "nvidia"
VendorName "Videocard Vendor"
BoardName "NVIDIA GeForce FX (generic)"
End Section
Remove other lines in this section..
Find these lines and delete them if they are there.. 
Load "dri"
Load "GLCore"
In the same section with all the Loads add this if not already there,
Load "glx"
Go down to the Indentifier "Screen" section...
Over there, you will find your onboard graphics card listed somewhere..
Replace it with "Videocard 0"
press escape and then :wq to save the file and close
press startx to check out if it works.. should work. worked for me
if it doesn't work.. try this.. i found it in some forum
vi /etc/modprobe.conf
add this line
alias char_major_195* nvidia
if there is something after nvidia (like nvidia-1-0..) delete it.. just let it be nvidia
also if there is the following line, delete it
alias nvidia nvidia-1...

should work now..
also i recommend downloading the latest NVIDIA linux drivers from the nvidia website.. 
To install these drivers, you must boot with "single" as argument
type init 2.. login with root
you must have gcc and kernel-devel installed. if your distro has selinux(i don't think ubuntu has it..) disable it.
cd to where you have the nvidia driver file
type this command..
sh NVIDIA(followed by the rest of the filename...type ls to view the all files or try NVIDIA* )
Driver installation should start..
Edit the /etc/X11/xorg.conf as shown above
Reboot.. should work now.

now.. i need to get my external wireless cdma phone modem to work with linux.. i heard there are solutions..

---

### Post by LordBug on 2006-02-08
Glad to see you solved it.  Very glad that you posted how to solve it, for others that might have the same issue later.

---

