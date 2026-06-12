---
title: "Returning to a running process in Terminal"
date: 2008-10-31
forum: General Help
---

### Post by cr0wn3r on 2008-10-31
Is there any way to return to a running process in the terminal window once the window has been closed?

If I start a cs server running for example, the logs continuously scroll up the terminal window and I can type specific admin controls straight in to the terminal as the process runs.

If I close that terminal window the process (eg the cs server) continues to run.

So I want to know if I can open a new terminal window and somehow return to seeing the process unfold in the foreground of the terminal window again...

Is it possible, and if so how do I do it?

---

### Post by Thomas Jensen on 2008-10-31
It is possible, there is a program for just this (and it's installed with Ubuntu by default). The program is called **screen**. I have only used it a little bit, but enough to cover your use-case...

Screen enables you to start a terminal program in a *virtual screen*, which can be detached from the terminal it was started from and later reattached to another terminal. You launch your server in screen by prefixing it like when use sudo:

```
screen csserver -abcd
```

When you want to detach the server process from the terminal you press **Ctrl+a followed by d**. This will bring you back to the command prompt.

You can now close the terminal window without killing the server. When you want to have a look at how the server is doing you find yourself a terminal and write this:

```
screen -r
```

This will reattach it. When you finally do close the server the virtual screen will close with it.

The reason for the cryptic command for detaching the screen from the terminal is to insure that it doesn't clash with the controls of interactive programs that one might be running.

Screen is apparently able to do a whole lot more than just this and if you're up it here's the manual:

```
man screen
```

---

### Post by cr0wn3r on 2008-11-17
Thanks for this info.

I had thought there might be a built in method without using another program, but I guess the best method is to not close terminal windows that youre using!

Thanks

---

### Post by bodhi.zazen on 2008-11-17
> **cr0wn3r said:**
> Thanks for this info.

I had thought there might be a built in method without using another program, but I guess the best method is to not close terminal windows that youre using!

Thanks

+1 for screen.

[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

But for your general job control question :

[http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/x5514.html](http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/x5514.html)

[http://www.network-theory.co.uk/docs/bashref/JobControlBuiltins.html](http://www.network-theory.co.uk/docs/bashref/JobControlBuiltins.html)

---

### Post by The Cog on 2008-11-17
> **cr0wn3r said:**
> Thanks for this info.

I had thought there might be a built in method without using another program, but I guess the best method is to not close terminal windows that youre using!

Thanks

Screen is great. You can logout completely and leave a process going, then log in and pick it up again later. I occasionally log in remotely, set something off in screen and disconnect again. I can go to another site and log back in to check on progress.

---

