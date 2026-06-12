---
title: "toshiba a305d-s6848 (ati x1250) 9.10 live cd results"
date: 2009-12-17
forum: Hardware
---

### Post by n2sins on 2009-12-17
[SIZE=2]this is a little info for ppl who want to know before they download if it will even work on the live cd.. i wasted lots of time trying to find out if this pc would even run karmic. right now im on karmic live cd.. so all the info is from the live cd and probably will be different once a real install is done.. but here are the things i found so far.. i normally run 9.04 and can do almost anything except games under 9.04 the temps get to hot.. well karmic has the same issue.. that appears not to have changed.. i use a huwaie e160 gsm usb modem.. i found i had to boot the live cd with it in the usb port to work.. it took a while to figuere out why it didnt work.. first.. you cant have any 1.1 usb hubs on it.. or it will not work.. it will say connected look connected but will not get on internet.. i had to unplug my hub.. 2nd whatever the defaults are for your gsm just save them in your network configuration and save and exit.. after that open and edit the connections.. to suit your network.. do not use the hub as it will disconnect you from the network..  using gkrellm and the dmesg i found that my cpu is 10c hotter then reported by gkrellm.. under the dmesg i seen a warning that it wasnt being read correctly.i checked  /proc/acpi/processor and looked at the temp 10c higher then reported. 9.10 has the lack of thermal triggers , and only shows the critical 105c. no change there. i will include the dmesg for both 9.04 and 9.10 so you can see.. remember alot of the dmesg has to do with the usb  as my hub seems to conflict with the usb gsm. i cant try network or wireless as i do not use them also  here is my read out for glx for the ati 1250 video chip
~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project
after getting the little things working it seems quite do able.. the fan still states off under/ acpi/thermal  and pfa1 still reports off.. but the processors state 8 throttle states.. 9.04 says none after custom dsdt.. acpi seems to work. i can adjust screen brightness and the soft touch buttons atleast work mute. i didnt try hibernate or suspend as i dont know if they are supported in live cd.. the temps is the only thing bothering me.. it isnt reading the temps right.. and 9.04  atleast read the temps correctly.. and 8.04 wouldnt even install.. it hangs.. 8.11 seems to install and run cooler.. i already had 9.04 . i hate to uninstall and reinstall older software that might have other problems i didnt see in the live cd..  i havent decided to try 9.10 yet.. also the bios bug is still reported under 9.11 .. one last thing.. i tried the dsdt edit and it found 0 erros 0 warnings and 15 optimizations.. so dsdt data isnt bad atleast with this ( a305d-s6848).. under 9.04 i seen no improvements running custom dsdt.. i was told 9.10 doesnt use custom dsdt so cant make a comparison. one last comment.. i did try the newest open suse.. it fails at hal. the only way to get to kde was to hit ctrl+c  then no keyboard or mouse just frozen welcome screen.. thats only included  for people thats looking for the right distro of linux to run on their pc.. im  a noob to linux but played with it for a long time.. just finally gave up on windows.. hopefully even if i didnt get it all right someone can look at this and gain some insight and help someone else.. as i am only able to provide some info and no answers.. atleast i try to help people..
[/SIZE]

---

### Post by n2sins on 2009-12-21
[COLOR=DarkRed][SIZE=3]so now i installed using the 9.10 alternate disk....

[COLOR=Black][SIZE=2] well, the disk asks u if u want to use internet i chose no... in the philippines the internet is not very good.. especially when using gsm usb modem..
well, the install disk does get the kernel and x configured.. this still irritates me.. after installing and rebooting.. i looked in my update manager and it said i needed to do a partial upgrade.. and a partial is 700 + meg..  that irritated me.. under docs it says you can upgrade using the alternate disk without internet.. that is true but not completely as many of the core components could not be installed using alternate disk.. so after 15 hrs of downloading and im not kidding.. it finally and luckily completed.. i never seen my internet run for any longer then 3 before the carrier boots you.. 

lets get to some specifics.. after the initial install.. everything looked decent
video works good. sound works ,but kk doesnt allow you to set sound events and from what i read its how it is and only can download themes if you can find them.  my only major problem was my usb.. the usb ports conflicted with each other.. if i had my mouse hooked up no gsm modem.
that took me a while to figure out why my internet was connected but no internet.. or upgrade with manager.. so after the partial upgrade.. my only problems is its reporting in dmesg error attum 141 not reporting temps correctly.. it appears that it is running cooler.. as the case isnt as warm but cant be sure yet.. also if running cpu on demand when the cpu switches to next level the sounds in the app disapear and when u leave the app must use system monitor to turn off the app.. so set your processor b4 running your app.. also my gsm modem seems a little confused.. it takes like 3 times to hook to the internet and actually get a page.. it will say connected each time but no data transfer.. 1 last problem that i have noticed is the old grub doesnt much like 9.10.. as each time it seems to have to search for the way to boot.. this takes about 7 seconds.. after that all is good... if you update like i did also remove your battery b4 running upgrade.. bc after the upgrade for some reason when you reboot it will show the bios page and the next page will be a _ and stop there.. remove the battery and it lets the memory go b4 the next boot.. so it will boot to grub..  right now runnning 9.10 kk with kernel 2.6.31.17

problems that kk fix from jj kernel..  the kernel fixes the 690 south bridge issue for sata.. also fixes the sd sr in dmesg and cpu throttling as being recognized. temp could be lower.. but the cpu temps from sensors cant be considered accurate according to dmesg.. all in all kk seems to be a little better on opengl test that i done.. smoother, higher details and maybe a little better frame rates too.. but this is subjective as i have no accurate way to prove this..

so if you have waited and you have the toshiba a305d-s6848 and you want a good report before going to kk.. give it a try.. so far to me jj seems as good if not better.. the acpi still isnt showing fan on until a suspend is done.. so it seems it has almost the same version of acpi.. maybe a bit better.. anyways have fun...
[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by n2sins on 2009-12-26
well , after less then a week and countless hours of playing with kk (klepto kangaroo) its time to put it down.. klepto= sound is always being stolen from apps.. kangaroo because all the simplest video games is now jumpy and unable to see the characters through the games background.. lets not even get started on all the have toos to get my gsm usb modem working.. 20 minutes to get online.. gosh.. and when you try to close an app.. you have to go through the system monitor to get it to quit.. whatever they done.. i would rate this as the worst version of ubuntu i have ran.. my first being 7.04.. so now time to kill this roo and get back to the stable jackalope..:( or try suse.. not decided

---

