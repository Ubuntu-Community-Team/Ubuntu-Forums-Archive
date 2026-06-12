---
title: "compaq problem"
date: 2005-02-27
forum: Hardware &amp; Laptops
---

### Post by lucan on 2005-02-27
hi,
i'm new to linux, and i just install ubuntu on my compaq (armada e500) laptop.
during boot up there are several line running on the screen with this error message :
starting hotplug subsystem.....
fatal error.... ( and it goes too fast for me to copy it down).... operation not permitted...
and after i login ubuntu cannot find the network card (linksys notebook adapter) i put into the PCMCIA slots. it also show me the battery at 0%.
best of all, when i log out, it wouldn't shut down, just hang down there. i have to remove the battery to forcely shut it down.
how can i fit it?  :confused: 

thanks.

---

### Post by hashimoto on 2005-02-28
You will probably find help to the "fatal error.." issue here: 
[http://ubuntuguide.org/#modprobefatalerror](http://ubuntuguide.org/#modprobefatalerror)

And regarding the shutdonw issue. look here:
[http://ubuntuguide.org/#acpipoweroff](http://ubuntuguide.org/#acpipoweroff)

Someone else has to help you with the battery and NIC issues.

---

### Post by lucan on 2005-02-28
hi,
thanks for the tips but i have already read that, the only problem is i don't understand what it say.

"$ sudo cp /etc/hotplug/blacklist /etc/hotplug/blacklist_backup"
"$ sudo gedit /etc/hotplug/blacklist"


Depends on the Error shown, append the following lines at the end of file 
pciehp
shpchp
hw_random"


when/where do i do this sudo thing? how and where do i add this append thing?
now i really understand why people say linux is not ready for basic user.

---

### Post by hashimoto on 2005-02-28
OK, let's take it easy, you can do it quite well.

The first two commands need to be run in a terminal window. You can find one on the menu Programs > System tools (if my memory serves).

When the termial window has opened, click on it to make it active, then write the first command (not the $, it should be there already, start with sudo...). Then press enter. It will ask for your user password, so type it in. The first command line just makes a safety copy, so you wont see nothing else. The cursor just jumps to the next line.

The second command opens a text file named "blacklist" in an editor named "Gedit". Your password won't be asked this time (linux already knows that you have the root privileges now).

To know what to add to the end of that file you need to be quick in reading the error meassages when booting. You probably have messages complaining about pciehp and shpchp. Go to the end of that file and simply add the corresponding lines at the end. Do not add hw_random if you don't get a boot error on that. Then save the file. You are now done.

The errors are actually harmless, so you don't necessarily have to do anything about them.

And you are right, linux does take more effort, but:
1) you will find a very helpfull community here so when ever you need help/advice, you're welcome and
2) with time you will learn a lot about your system

I'm also convinced that in the future linux will be more beginner friendly (Ubuntu is already a big step to that direction). It just takes some time. I also try to remember that much of the work is done by those great programmers just for the fun of it. I'm certainly grateful for them for doing that and giving us this great OS!

---

### Post by lucan on 2005-02-28
hi,
I do know that much of the work is done by those great programmers just for the fun of it and in their own free time. I'm certainly grateful for them for doing that too plus you for helping by explaining it to me. and i'm not easily giving linux up yet.

but i do have questions, 
1) the solution that you have teach me: do it solve the problem or just disable the hotplug subsystem?

2) correct me if i'm wrong; hotplug = PCMCIA slots.
is it that why my network wireless card cannot be detect?

3) is there any books i can refer to? i cannot not keep asking for help, cause i need to understand what does pciehp, shpchp and hw_random means, and many others alien term.

---

### Post by hashimoto on 2005-02-28
1) As I have understood the situation (and this is very unscientific and probably less accurate explanation): hotplug tries to load these modules during start. You get the error messages because your harware does not need/support these modules. Adding the lines to blacklist basically tells the hotplug: "Don't bother with these modules". Otherwise the hotplug continues to work.

2) My understanding: also USB, CDROM etc.

3) Sorry, can't help with the book. I have never read one single book about linux, so I can't recommend. My only way to get help has always been through this board (other boards before Ubuntu was born) and Google. I wonder if the books actually stay up to date as linux is developing rapidly and new features get included. I might be wrong, though. Maybe someone more educated can step in and shed some light?

---

### Post by cr4z3d on 2005-02-28
hey.. i'm getting one of those fatal errors. but not one of them that's on the help site. it's for my floppy drive.. but i don't eve have a floppy drive and it tells me this. is there a way to fix this? i haven't been able to get it to start and go past that error yet..

---

### Post by lucan on 2005-02-28
thanks for the tips hashimoto. i'll try it.

but i still have question and finally copy the error after copy, reboot, copy, reboot,copy....:
1) when boot, " ide2:i/o resource 0x3EE-0x3EE not free
                       "ide2: ports already in use, skipping probe"
what is that?

2) modprobe" fatal: error inserting pciehp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp. ko):operation not permitted
    modprobe" fatal: error inserting shpchp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp. ko):operation not permitted.
but at the right, it show [ok]
can i still do what you teach me?

3) since hotplug also means cd-rom, USB and even floppy drive which my laptop has no problem running it , if i add in the lines to blacklist. will that cause the cd-rom, USB not to work?

thanks

---

### Post by lucan on 2005-03-01
k, i will be answering my own question so if anyone who is as blur as i am are reading this will know what's happening.

1) i still don't know what  'ide2:i/o resource 0x3EE-0x3EE not free'
                                      "ide2: ports already in use, skipping probe" means. i remove the cd-rom when i bootup and this sentence still appear, same when i remove the floppy drive. the only thing i know is, this sentence seems harmless cause my floppy and cd still work.

2) modprobe" fatal: error inserting pciehp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp. ko)operation not permitted
modprobe" fatal: error inserting shpchp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp. ko)operation not permitted.
i have remove it when bootup and later put it back on. this modprobe is a harmless sentence also. my PCMCIA slots is working cause the wireless card show up in the device manager, but the wireless icon still show no device. that means ubuntu don't detect it. 

now, i'm need to solve the shut down problem. i still need to remove the battery in order to switch off the laptop, also find way for the wireless card to connect to the internet.

anyone can advise?

---

### Post by lucan on 2005-03-05
finally, the battery works. i upgraded my BIOS. reinstall Ubuntu. the battery icon now show the battery bar, and shut down like windows.  i like it! the only thing is the battery goes flat under half and hours time.

now i left with the wireless problem. i'm thinking of using wine to get the wireless device driver. can anyone teach me how to install that in ubuntu and run it?

Thanks.....

---

### Post by ph00dz on 2005-03-06
Here's how you install windows wireless drivers:

[http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation)

---

### Post by andyk on 2005-03-07
i got wifi to work in literally 10 minutes this morning on my compaq notebook.
usin the broaddcom 94306 chipset

open terminal, and type:
[I]
sudo apt-get install ndiswrapper-utils[/I]

*sudo ndiswrapper -i xxxxx.inf* (path to your wifi driver) (check ndiswrapper @ sourceforge for proper drivers if needed)

*sudo modprobe ndiswrapper*

that should bring up wifi.  go to network settings and make new profile for wlan0 (wifi)
once that is set open gedit, then open /etc/modules/

at the bottom add of the list add *ndiswrapper*.  save and restart.  Voila!  (in theory)

---

### Post by ironikhq on 2005-03-15
[QUOTE=lucan]finally, the battery works. i upgraded my BIOS.[/QUOTE]

can u describe exactly what u have done, 'cos i have the same problem with my hp pavilion dv1000. (battery status not working)

ty.

---

