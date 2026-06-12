---
title: "How do you use rsjog on a Sony laptop?"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by eeefresh on 2006-06-10
I am trying to the jog dial on my Sony Vaio PCG-GR300 laptop to work with Dapper.  When I searched the forums, I discovered rsjog, which looks like a cool program.  I downloaded it from the repositories, but I am not sure how to use/activate it (I'm new to Linux, so please be kind!)

It's installed, but where do I find it?  Just turning the jog dial doesn't seem to do anything, so I am assuming I have to activate it somehow.  Can anyone help?

---

### Post by eeefresh on 2006-07-31
Okay, I found some instructions in the Install file, but I don't quite understand how to configure everything. The FN keys are working, but the jogdial still doesn't do anything. Can anyone help? It looks like sucha cool utility, I just can't get it to work right...

---

### Post by eeefresh on 2006-08-01
Here is what I see in the install file(in bold):

[B]You'll need:
ruby
libgtk-ruby
xlibs-dev (the X11 library headers)
The X11 XTest extension (don't worry, you should have it built in)
spicctrl (to change the brightenss of your lcd screen)
aumix (to change the volume)[/B]

I believe I have all these since I downloaded through Synaptic.

[B]Then just:
make
su -c "make install"[/B]

I don't understand this. When I paste it into terminal, I get this:

[I]doug@doug-laptop:~$ su -c "make install"
Password:
su: Authentication failure
Sorry.
[/I]
[B]And copy the sample .rsjogrc and .rsjog.menu to your home directory and
tweak.[/B]
Did this, but as I said, I am having trouble figuring how to tweak.

[B]Run rsjog from your .xsession like this:
rsjog &[/B]

Not sure what this means at all. How do I run from .xsession? What is it?

Thanks in advance for the help. I am a Linux/Ubuntu newbie, but I appreciate the support!

---

### Post by eeefresh on 2006-08-01
Anyone?

---

### Post by Toufik on 2006-08-03
To be sure, run in a terminal

```
sudo apt-get install ruby libgtk-ruby ...
```

For the installation, 
```
make
``` means that you compile the program (create the executables)
```
su -c "make install"
``` meens that you install the program, therefore you need to be root.  su is a command which allaow you to switch to the root account.  Damned!! The root account is not active under Ubuntu (it has no password)!!  That's your error.  Try instead
```
sudo make install
```

Now you have to launch the program at each startup, there is different way of doing it.  If your not familiar with Linux, use the graphic one :D
In Ubuntu Menu > Preferences > Sessions > Startup Programs, you can add program executed at each startup.  Just write rsjog

You only need the & if you launch it from your terminal, it meens "execute in background".  Therefore, here, it is not nexessary

I hope it helps

---

### Post by eeefresh on 2006-08-07
Thanks a lot!  I'll try this out and let you know how it worked!

---

### Post by eeefresh on 2006-09-02
I'm still getting stuck on the actual install.  Or do I even need to do an install in Terminal?  I already installed rsjog and the relevant files via Synaptic.  I also made sure ruby was the latest version.

When I try to "make" in terminal it gives me more errors.  What *exactly* should I type in termina to compile this?

---

