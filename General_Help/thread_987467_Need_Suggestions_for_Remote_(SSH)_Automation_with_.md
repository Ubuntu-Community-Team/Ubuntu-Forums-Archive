---
title: "Need Suggestions for Remote (SSH) Automation with C#"
date: 2008-11-19
forum: General Help
---

### Post by arcticool on 2008-11-19
My office uses C# so they'd prefer I did my testing of this Linux box through my XP desktop. I have connected to the Linux machine and done all manual testing so far with Putty. Now I need to automate the sending of these commands and receiving of feedback into if/else structures which generate new commands sent back to the Linux command line through SSH. I am not a seasoned programmer but pretty confident I can get the test logic done in C# but I need some way to handle the SSH connection and retrieval of feedback. 

Apparently Putty does not provide an API.
This is quite a problem since using Putty for automation will require some kind of keyboard emulator to send the commands and then the reading of Putty logs to grab feedback. This will have latency and will require time waits and could get ugly and unreliable really quick.

Long question made short- any suggestions for an SSH connection tool that provides an API that will work with C# without too much tooling? Feedback much appreciated.
Thanks in advance,

JR

---

### Post by Portmanteaufu on 2008-11-19
I've never written anything in C#, but maybe this alternate approach could help you. You can install Cygwin, which is a freely available set of Linux tools written to run on Windows. Then you can use *their* version of SSH instead of putty; the benefit here is that the Cygwin SSH command allows you to execute a command following login and putty (to the best of my knowledge) does not.

Once installed, you can write programs / scripts in any language on the linux box. For this example, I made a bash script called "cmds":

```

#!/bin/bash
touch file1
touch file2
touch file3
exit 42

```

then I made it executable with:
```
chmod 755 ~/cmds
```

Then, from the windows box, (in the cygwin bash shell,) I ran: 
```
ssh <username>@<ipaddress> '~/cmds'
```

Immediately afterward, I ran:
```
echo $?
```
Which showed the exit status of the previous command; here it was '42'.

By doing "ls" on my linux box, I was able to see that file1, file2, and file3 had all been created successfully indicating that the script had indeed ran.

You can place the exit status in an if structure to indicated to the windows box what needs to happen next.

Hope that helps!

---

### Post by arcticool on 2008-11-21
Thanks but I'm really stuck with the C# framework. It's a work requirement. All I need really is a way to drive a Linux command line interactively from a Windows box with C#. It's too bad Putty doesn't expose an API...

---

### Post by arcticool on 2008-11-28
Anyone? I'm really under heat to get this project completed and I haven't even gotten off the ground yet. There must be *some* way to drive the Linux shell with synchronous communication from C#.

---

