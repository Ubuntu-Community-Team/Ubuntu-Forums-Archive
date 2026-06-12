---
title: "Can a background process simply vanish?"
date: 2008-08-08
forum: General Help
---

### Post by projetomanager on 2008-08-08
Hello.

I have two unrelated executables that I started like this:

1) opened a ssh shell

2) Started the two applications

$ mfsrv &
$ chatsrv &

3) Exited the shell

$ exit

Today when I logged in to my server both were gone!
Both programs are written by myself. chatsrv runs an endless loop and never terminates programmatically.
mfsrv terminates programmatically but it prints a message in the log. No message was there.
I made the following checks:

1) Checked core dumps
I found no cores.
My ulimit is set to 'unlimited', and my system is set to dump cores in the cwd.
None of these processes ever changes the cwd. I wouldn't be suprised if one of them had cored.
But both! They are totally unrelated.


2) Checked if the system had rebooted
last boot

it didn't reboot

3) Check if someone else had accessed my server

last -x

I was the last one to access the server.

What is going on?

Normally 'ps -eaf' prints this, when the 2 processes are running:

UID        PID  PPID  C STIME TTY          TIME CMD
mfoot     7937     1  0 13:17 ?        00:00:00 ./mfsrv
mfoot     8012     1  0 13:21 ?        00:00:00 ./chatsrv

Is the kernel terminating my processes?

---

### Post by HermanAB on 2008-08-08
Check to see whether they get terminated when you exit ssh.  (Do that by running two ssh sessions).

---

### Post by damoxc on 2008-08-08
They will do unfortunately, i think if you run them as ```
bash -c 'command1 &; command2 &' & 
```that will fix it

---

### Post by kihjin on 2008-08-08
Consider using 'screen'

$ apt-get install screen

then do

$ screen -d -m -S mfsrv mfsrv
$ screen -d -m -S chatsrv chatsrv

now you can access the screen

$ screen -r mfsrv

will show you output for the command. to return back to your original tty enter the key combo CTRL+A d (aka ^A d) You don't need to hold CTRL when pressing d.

---

### Post by sdennie on 2008-08-08
You may also be able to fix the problem by disowning the servers from the parent shell:

```

mfsrv &
chatsrv &
disown -a
exit

```

As mentioned above, using screen is also a nice solution.

---

### Post by projetomanager on 2008-09-04
When I exit the shell they never vanish. I then use a windows client to connect to both processes usings sockets and they are live. One process is a game server and the other a chat server. For 2 times, after more than a week running, these processes vanished without a trace.
I am going to daemonize them properly, but I still would like to know the technical reason why I can get away with running them for a while just exiting the shell, and why they are terminated.

---

