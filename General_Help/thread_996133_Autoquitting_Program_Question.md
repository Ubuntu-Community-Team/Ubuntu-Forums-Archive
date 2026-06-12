---
title: "Autoquitting Program Question"
date: 2008-11-28
forum: General Help
---

### Post by aeroace on 2008-11-28
So I have tried for a while now to get a program to run with a keyboard shortcut. I can get it to start but after it loads, it automatically quits. Now I am fairly new to Ubuntu so I really don't know how to troubleshoot this. The only other time I have experienced a program quitting on me is when I X out of the terminal I have started the program with (with or without running the program in the background). I am thinking that this is somehow related to this. 

I personally think that the program is quitting because the keyboard shortcut runs the following command: matlab & 
This command is normally entered in a terminal window but if one isn't open than it kills the newly open program just as if you X'ed out of the terminal. Is this logical thinking?? And if it is, is there any way around this to get the keyboard shortcut to work? Any ideas are greatly appreciated, and as always thanks a ton! 

-- aeroace

---

### Post by soro2005 on 2008-11-28
Depending on where's your matlab, you may have to include the full path in your shortcut launcher. (E.g. /bin/matlab).

*Edit* Sorry, that's nonsense. Obviously, the path is not the problem. Are you sure that there's no problem if you start it from a terminal? That's normally where you can see the errors that are being thrown. Also, how are you binding the keyboard shortcut? You shouldn't need to use the &. I don't think it should do harm, though.

---

### Post by aeroace on 2008-11-28
If I run MATLAB directly from the terminal there are no errors thrown. I'm not quite sure what you mean by my binding method, so my apologies if I don't give the answer your looking for. I run gconf-editor and go to /apps/metacity/global_keybindings and assign run_command_1 <Control><Alt>m. 
I then go to /apps/metacity/keybinding_commands and assign command_1 a value of matlab &. If I don't add the & I get the same result.

---

### Post by soro2005 on 2008-11-28
Two questions:

1.) What happens if you run matlab from the "Run application" dialog? (<alt>+<f2>)

2.) In the terminal, can you start matlab from any working directory, or do you have to navigate to a specific one?

I have no experience with matlab, but from what I see it's a program with a gui and should not require to be started in a terminal. It might require to be started from a specific working directory, though. Normally, the application starter should take care of that. But perhaps, something has gone bad with the installation.

Additionally, you could try to assign a shortcut to, for instance, gedit and see whether that works. Just to locate the error. Also, you could tell us how you've installed the program, and the output of
```
which matlab
```

And in any case, I'm quite convinced that, what you really want is not a keyboard shortcut, but [Gnome Do](http://do.davebsd.com/).

---

### Post by aeroace on 2008-11-28
> 1.) What happens if you run matlab from the "Run application" dialog? (<alt>+<f2>)
This causes the same result as the keyboard shortcut, meaning MATLAB starts, then immediately quits. Hummm.... 

> 2.) In the terminal, can you start matlab from any working directory, or do you have to navigate to a specific one?
I can start MATLAB successfully form any working directory, it does not matter where I am if I start the program form the terminal. 

Using the code: which matlab results in:
/usr/local/bin/matlab

matlab here is a symbolic link pointing to 
/usr/local/matlab/bin/matlab

At this point I agree with you in that making a keyboard shortcut probably isn't the best way to go. I actually have a shortcut to quickly start a terminal window (maybe I'm just too addicted to starting things from the keyboard), and can easily start MATLAB from the terminal. I would just like to ensure that there isn't a big issue with my installation. Also I don't know what the significance of this is, but when I first installed MATLAB I had some permission problems I had to take care of. I still have an error log from when I first did the installation which has been added below:

java.io.FileNotFoundException: /home/my_user)name/.matlab/R2008a/MATLABDesktop.xml (Permission denied)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
	at com.mathworks.mwswing.desk.Desktop.saveLayout(Desktop.java:3446)
	at com.mathworks.mwswing.desk.Desktop.close(Desktop.java:3938)
	at com.mathworks.mwswing.desk.Desktop$DeferredCloser.run(Desktop.java:4014)
	at com.mathworks.mwswing.SynchronousInvokeUtility$SynchronousEventAdapter.executeOnSwingThread(SynchronousInvokeUtility.java:94)
	at com.mathworks.mwswing.SynchronousInvokeUtility$SynchronousEvent.run(SynchronousInvokeUtility.java:112)
	at com.mathworks.jmi.AWTUtilities$Invoker$4.runWithOutput(AWTUtilities.java:409)
	at com.mathworks.jmi.AWTUtilities$Invoker$1.run(AWTUtilities.java:331)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)

---

### Post by soro2005 on 2008-11-28
I think there's something messed up with your installation. /usr/local/matlab/bin/matlab does certainly not look like it's where it should be normally. The structure inside /usr/local mirrors roughly the one at /usr, so the binary would belong into /usr/local/bin/matlab perhaps. It looks to me like, perhaps, you've tried to install twice, and there might be some duplicate stuff...

Ideally, you install it into /opt to keep your system clean. If possible, I would recommend you uninstall the program completely, then start all over and make sure it installs correctly.

The error you quote is from installation or from first start? Looks more like the first start.

Do you have a start menu entry for matlab? Does it work? If yes, you could figure out how to launch it correctly by having a look at the menu entry (by running alacarte).

To catch the error that's crashing it, you could also try to write the output to a file. Start it from <alt>+<f2> like this:
```
matlab > /home/yourusername/Desktop/matlab.log &2>1
```
Not sure whether this produces anything interesting, though.

---

### Post by aeroace on 2008-11-28
soro2005, thank you so much for your help as I am still in the Linux n00b phase. I will try making the log and looking at whats really crashing the program but ultimately I might take your advice and reinstall it correctly. Your help has been great, I think you make have sold me on GNOME Do as well. Thank again!

---

### Post by soro2005 on 2008-11-28
Gnome Do is the new keyboard shortcut. 8) Or rather, it's like all the shortcuts you could want without ever configuring them.

---

### Post by patiepp on 2010-03-27
try 
matlab -desktop
command.MAtlab will not quit that way.
For Java problems ensure you have installed sun-jre package 
execute
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre

or better you can use script
 	Code:
 	#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre
matlab -desktop

---

