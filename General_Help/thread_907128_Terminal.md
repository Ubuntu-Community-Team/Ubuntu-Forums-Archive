---
title: "Terminal"
date: 2008-09-01
forum: General Help
---

### Post by Bergs on 2008-09-01
Just wondering what my problem could be?

I only just installed Ubuntu today and so far it's been a breeze, but this just isn't adding up right, I followed direction found by the creator and now it's coming up with this.

If you need any more information on what I was doing just ask and I'll gladly step you through it.
--------------------------------
jsl@jsl-laptop:~/BNU$ ./run.sh
Killing BNUBot from PID file
kill: 14: No such process

kill: 14: No such process

java process could not be stopped!
---------------------------------

Site I got it from: [http://code.google.com/p/bnubot/wiki/Downloads](http://code.google.com/p/bnubot/wiki/Downloads)

Thanks,

Bergs

---

### Post by natirips on 2008-09-01
It tries to kill a process running on your computer, but why would a "chat" client want to kill the process is beyond me. Try downloading from another site (google for it). You've probably downloaded some broken version (unless this happened while exiting the program?).

---

### Post by forger on 2008-09-01
probably wants to kill other bnu-bots running..
can you post the output of:
```
ps aux > /tmp/pids.txt; cat /tmp/pids.txt
```
It will show information about your currently running processes

---

### Post by forger on 2008-09-01
The run.sh is the following:
```
#!/bin/sh
PIDFILE=bnubot.pid
if [ -f $PIDFILE ] ; then
	echo 'Killing BNUBot from PID file'
	PID=`cat $PIDFILE`
	kill -3 $PID
	if kill -9 $PID ; then
		echo "java process stopped"
		rm -f $PIDFILE
	else
		echo "java process could not be stopped!"
		exit
	fi
fi

echo "starting a new one"
java -cp `ls -1 lib/*.jar | tr '\n' ':'`BNUBot.jar net.bnubot.Main -logfile log.txt 2> stderr.txt &
pid=$!
echo $pid > $PIDFILE
```

I think you have two options here:
1) You could try manually killing the process:
```

kill -9 `cat bnubot.pid`
killall -9 -r '.*java.*'
rm bnubot.pid
```
and run the bnubot again:
```
bash run.sh
```

2) I would suggest to remove the installation folder, and reinstall it.

---

### Post by Bergs on 2008-09-01
Thanks mate, your second solution fixed the problem.

I'm glad there are still people in the world who can give the correct answer without to much messing about :P.

---

### Post by forger on 2008-09-01
You should've posted the contents of run.sh - You would probably get a faster reply when you lay out all the necessary info ;)

---

