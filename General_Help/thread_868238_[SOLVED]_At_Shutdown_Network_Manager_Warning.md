---
title: "[SOLVED] At Shutdown Network Manager Warning"
date: 2008-07-23
forum: General Help
---

### Post by penguins01 on 2008-07-23
Hello,

Whenever I have been logged into my computer, and then go to shut it down, the network manager gives me a huge wall of text pretty much, but then shuts down before I can read most of it.

I managed to write down most of the message, and google it for help, but there didn't seem to be anything on it.

The message goes as follows:

Network Manager: <WARN> nm_signal_handler(): Caught signal 15 shutting down normally


Network Manager: <Info> Caught termination signal

Network Manager: <debug> [1216843827.868190] nm_print_open_sockets 
List:

Network Manager: <debug> [1216843827.868387] nm_print_open_sockets
List done.

Network Manager: <WARN> nm_hal_deinit(): libhal shutdown did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, or the network connection was broken.

I do not know if this is just a normal warning, something I need to fix right away, or how to fix it.


Also, I noticed that this might be similar to a few other posts, such as [http://ubuntuforums.org/showthread.php?t=686123](http://ubuntuforums.org/showthread.php?t=686123) Titled Message Bus Daemon.

Any help or information would be appreciated.

---

### Post by avtolle on 2008-07-23
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29) if the message display bothers you. I have (had) it too, and following the link took care of the messages appearing. It seems to not be a real problem, BTW.

---

### Post by penguins01 on 2008-07-23
Thanks very much!

I wasn't extremely worried, but since something seemed to be wrong, I'd figure I would check it out and see.

---

### Post by wjwh on 2008-07-23
> **avtolle said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29) if the message display bothers you. I have (had) it too, and following the link took care of the messages appearing. It seems to not be a real problem, BTW.

I have this problem also - and, unfortunately, this so-called fix does absolutely _nothing_ for it! Does anyone know of another solution that really _does_ work?  I have tried all that I could find on the "Known Hardy bugs and workarounds" thread - [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851) - and have still not found one that works on my system!

---

### Post by carl_pr on 2008-07-24
wow awsome, im having this same issues. I dont know if this is bad or not ubuntu runs perfect but those warnings are scaring me. I been days trying to make a thread about it but well my english aint that good and i dont know what the warnings say because they dissapear fast.


hope this help me

---

