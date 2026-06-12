---
title: "[SOLVED] Starting an application from terminal yet &amp;quot;detached&amp;quot;"
date: 2008-11-11
forum: General Help
---

### Post by Ezetreal on 2008-11-11
I've looked around quite a bit for the answer to my question but the problem is I don't know what search term to enter (if i did I think i would have had my answer).

Now for the question. I was wondering if anyone new of a command I could insert that would allow me to launch an application from the terminal (as opposed to Alt F2) yet allow me to close that terminal without closing the application. I know about the "screen" command, but that is more annoying than Alt+F2.

I thought about words like "detach" or "uncouple".

For example:

$detach nm-applet     

--->  That would allow me to launch nm-applet from  terminal and then close the terminal yet still have my internet connected!

Thanks for your help.

---

### Post by ju2wheels on 2008-11-11
Launch the application and put an ampersand (&) at the end of the command such as:

```

> firefox &

```

This would allow you to launch Firefox from the command line and close the terminal afterwards.

---

### Post by spibou on 2008-11-11
I think the background job will still receive a SIGHUP when Bash itself receives SIGHUP (which it will when the terminal closes). But the disown builtin fixes that.

---

### Post by Ezetreal on 2008-11-11
Thanks ju2wheels !

The ampersand works great to launch multiple applications from the same terminal. However if you close that terminal from the gui (as opposed to typing "exit" in the terminal, the application will close.

Thanks to your reply, I was able to find "nohup" which allows you to close the terminal after launching the application. 

$ nohup amarok

This will launch amarok and allow you to close the terminal without ending the application.

You can also use both nohup and & at the same time.

Note:  I tried both of these with vlc media player with no success. I think it might be an issue with the new vlc (0.9.4) or with intrepid because I have found sites where they used "nohup vlc" as the example and it apparently worked.

Thanks again Ju2wheels, 

Hope this helps anyone.

---

### Post by ariel on 2010-06-18
> **Ezetreal said:**
> Thanks ju2wheels !

The ampersand works great to launch multiple applications from the same terminal. However if you close that terminal from the gui (as opposed to typing "exit" in the terminal, the application will close.

Thanks to your reply, I was able to find "nohup" which allows you to close the terminal after launching the application. 

$ nohup amarok

This will launch amarok and allow you to close the terminal without ending the application.

You can also use both nohup and & at the same time.

Note:  I tried both of these with vlc media player with no success. I think it might be an issue with the new vlc (0.9.4) or with intrepid because I have found sites where they used "nohup vlc" as the example and it apparently worked.

Thanks again Ju2wheels, 

Hope this helps anyone.

nohup your-app &      #made my day :) 
Thanks!

---

