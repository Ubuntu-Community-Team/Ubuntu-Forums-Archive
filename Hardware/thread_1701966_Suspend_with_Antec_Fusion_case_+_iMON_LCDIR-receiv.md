---
title: "Suspend with Antec Fusion case + iMON LCD/IR-receiver help"
date: 2011-03-07
forum: Hardware
---

### Post by gunnarflax on 2011-03-07
Hi! I'm trying to get suspend/hibernate to work on my XBMC Live 10 (ubuntu 10.10). I have a Antec Fusion Remote case with built in iMON LCD/IR-receiver. The thing is that the LCD/IR-receiver is preventing the system to hibernate and that kinda sucks. The other problem is that when the system is turned off the LCD-screen still lights up the whole room. I found two possible solutions to this problem and one is [this one]("http://askubuntu.com/questions/25540/suspend-fails-and-i-know-the-module-causing-it-what-can-i-do"). But I think that only make the system skip unloading that module while the following user's post indicates that he has made it work as it should:
> **rodercot said:**
> Hi Gazer22,
  
  I just wanted to let you know I have updated the how-to for 9.10 Myth  or Karmic on getting the MCE remote working with ffdc device and then  using the MCE remote dongle to transmit commands on the same machine. 
 
  Two days later it is working. UGGHHH. I am working on suspend now, when  I get that all figured out I will update again. here is the link. 
 
  [http://ubuntuforums.org/showpost.php?p=8860349&postcount=11](http://ubuntuforums.org/showpost.php?p=8860349&postcount=11)
 
  **update on this**. I am actually making my life even more painful  by trying to get my Gyration Remote(all buttons) working with lirc_imon  and lirc_mceusb. So the gyration would pass commands, Lcdproc would  drive Lcd and the MCE dongle will transmit commands. So actually 4 lirc  device really as the gyration is two input events by itself, this is  proving the biggest struggle I have had to date with the setups. I will  post an update to the howto when complete. 
  
  another note - In my antec chassis, you can try this to if you like. to  setup suspending I enabled USB0 via sudo su - echo USB0 >  /cat/proc/acpi/wakeup - I added this line to my /etc/rc/local right  above the EXIT 0 line. Then I visudo to give access to my user to  /usr/sbin/pm-suspend. This allows my to run pm-suspend without sudo and  powers the system back on from my power button on the MCE 1039 remote. 
 
  All that said, if you do the above and it suspends OK then in LCDd.conf  set your backlight option to BLANK and your LCD will shutoff on  suspend. you can also add to your /etc/pm/sleep.d/ a 07LCDd script that  kills LCDd on suspend and restarts it on resume. If you are not sure  about that let me know and I will post a copy of mine for you to try. 
 
  This option shuts down LCDd on suspend, kills the backlight and the  power led on my Antec 430 Black case with any motherboard including ASUS  which have the boards that cause the flashing power led. 
 
  Regards,
 
  Dave
But I don't fully understand what he means and I've tried to make contact with him but had no success. All I want is that the system should be able to hibernate and when it hibernates or shut downs, the lcd screen should go black. Can anyone help me shed some light onto this problem?

---

