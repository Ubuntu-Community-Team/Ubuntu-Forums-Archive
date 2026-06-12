---
title: "Unable to boot Ubuntu 14.04"
date: 2016-07-24
forum: Hardware
---

### Post by Ashwin_D on 2016-07-24
I have a DELL Vostro 3800 and I do not have any other OS except Ubuntu 14.04 on this box. Since yesterday I am unable to boot my system

I get this when I switch on my Dell desktop

No boot device available
SATA 0: Installed
SATA1 : None
SATA 2 : Installed
SATA 3 : None

Strike the F1 key to retry boot. F2 to run the setup utility.


I have a USB copy of the 14.04 LTS and I inserted that into the USB drive and I keep pressing F12 and I get the option to boot from sandisk. It does the Ubuntu logo in violet
and then I see six dots and then it hangs. It does not go beyond that.

I ran Dell diagnostics and all tests came out successful. How can I solve my problem and be able to boot again ?

---

### Post by Ashwin_D on 2016-07-24
Will running the boot repair disk help ? 

[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I have a vague feeling that some graphics software that I installed corrupted the Master Boot Record. Hence I am unable to boot.

Are there any other solutions ?

---

### Post by yancek on 2016-07-24
Running the boot repair disk using the option to "Create BootInfo Summary" will provide details on the system.  Do not try to make any repairs but post a link to the output here and someone may be able to suggest something.  Also, exactly what 'graphics software" did you install?

---

### Post by Ashwin_D on 2016-07-24
Hello Yancek,
                    I was able to login to Ubuntu in the following way by pressing shift continuously. The problem is with X windows. I am not able to get a connection to X windows.

When I type /usr/sbin/lightdm start it says job unable to start. 

Can you help me now ?

---

### Post by Ashwin_D on 2016-07-24
Yancek - this is the software I installed along with it's dependencies - [https://www.vapor.ucar.edu/internal/downloads/source-distributions](https://www.vapor.ucar.edu/internal/downloads/source-distributions)

The last one I installed was this - assimp 3.1.1 and freetype 2.5.3. It all went through successfully and I was able to see the output and then it froze.

---

### Post by Ashwin_D on 2016-07-25
This one actually turned out to be a problem with X.

When I ran sudo startx $(which unity) I get
[COLOR=#111111][FONT=Consolas]usr/bin/X : error while loading shared libraries : libimf.so cannot open shared object file: No such file or directory

[/FONT][/COLOR]The display that I have is

VGA Compatible controller
product : 4th generation core processor family integrated graphics controller [COLOR=#111111][FONT=Consolas]vendor : Intel Corporation

[/FONT][/COLOR]obtained as a result of [COLOR=#111111][FONT=Consolas]sudo lshw -c display.

[/FONT][/COLOR]Any idea what shared library I must install to get my display going again ?

---

