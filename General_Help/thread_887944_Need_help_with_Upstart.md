---
title: "Need help with Upstart"
date: 2008-08-12
forum: General Help
---

### Post by gscott2112 on 2008-08-12
I tried asking this question on the Development & Programming forum a week ago but did not get any responses there so I am trying here.

I need a little help understanding the Upstart process. I have a program that I want to run as a service and I'm trying to use Upstart to handle it.  

I have a job file created and placed in /etc/event.d that 'seems' to start and stop the service. However when I try to manually start the service by executing the following

>sudo start myob

The command never terminates.  I have to interrupt the command to get back to my shell.  This isn't expected behavior is it?  From what I've read upstart doesn't require my program to daemonize itself, but when I modify my job file to have my program daemonize, the start command will actually return and my service is running.  The problem is that the subsequent stop command fails in that instance.

>sudo stop myjob
stop: Job not changed: myjob

What am I missing here?

---

### Post by hal8000 on 2008-08-12
Post the script you've added to /etc/event.d


sudo start myjob

will not return to a command prompt unless you start it as a background task.
sudo start myjob &

will start the task and return to a prompt. I would imagine its an error in your bash script thats causing the problem, start with any script in the event.d folder to use as a template.

---

### Post by gscott2112 on 2008-08-12
Post the script you've added to /etc/event.d


sudo start myjob

>>will not return to a command prompt unless you start it as a >>background task.

That's not the behavior I'm seeing with other services.
For example: sudo start/stop tty3  both return immediately

The job file i'm using can't get any simpler:

start on startup
start on runlevel 2
start on runlevel 3
exec /usr/local/myservice/myserviced

---

