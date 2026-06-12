---
title: "Problems fetching repositories... urgent!"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by sedgie on 2006-01-12
Hey guys,

I just installed Ubuntu 5.10 a couple of days ago, but I'm having trouble recieving repositories in Synaptic. First, I went to Settings>Repositories, and checked off the repos I wanted (namely the universe repos). Now, when I tried to fetch them, I got an error saying 111: Connection refused. I recognized this as a proxy problem, went to Settings>Preferences>Network, and put in my school's proxy server. Then, when I reloaded again, I got a 404 Object not Found when fetching packages. I switched to some of the other repos in Settings>Repos and no matter what site I was getting it from I got the 404. I then entered the repo package's URL in Firefox and it popped right up, so obviously the 404 is not a server side error. Anybody have any ideas?

p.s. first post yay

Thanks in Advance,
sedgie

---

### Post by Mr_Grieves on 2006-01-12
It's a server side error. 404 means - File/Page Not Found.

I think you have done something to the paths of the repositories :) You are connecting to the webserver, but it doesn't have what you're asking for..

Check the paths so that they are not faulty. You're perhaps best off to copy the names off a website wich publish them.

---

### Post by dcstar on 2006-01-12
[QUOTE=sedgie]Hey guys,

I just installed Ubuntu 5.10 a couple of days ago, but I'm having trouble recieving repositories in Synaptic. First, I went to Settings>Repositories, and checked off the repos I wanted (namely the universe repos). Now, when I tried to fetch them, I got an error saying 111: Connection refused. I recognized this as a proxy problem, went to Settings>Preferences>Network, and put in my school's proxy server. Then, when I reloaded again, I got a 404 Object not Found when fetching packages. I switched to some of the other repos in Settings>Repos and no matter what site I was getting it from I got the 404. I then entered the repo package's URL in Firefox and it popped right up, so obviously the 404 is not a server side error. Anybody have any ideas?

p.s. first post yay

Thanks in Advance,
sedgie[/QUOTE]
Try a Synaptic/system restart after changing the proxy settings.

---

### Post by sedgie on 2006-01-12
tried both.

---

### Post by sedgie on 2006-01-12
[QUOTE=Mr_Grieves]It's a server side error. 404 means - File/Page Not Found.

I think you have done something to the paths of the repositories :) You are connecting to the webserver, but it doesn't have what you're asking for..

Check the paths so that they are not faulty. You're perhaps best off to copy the names off a website wich publish them.[/QUOTE]

well, I have changed anything to do with the repos besides making the universe ones multiverse as well, but I'll try this anyway

edit: When I click on "edit" for each of the repos, they all have URIs of [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu). Is that right? Could anyone whos synaptic works see if their repos point there as well?

---

### Post by dcstar on 2006-01-13
[QUOTE=sedgie]well, I have changed anything to do with the repos besides making the universe ones multiverse as well, but I'll try this anyway

edit: When I click on "edit" for each of the repos, they all have URIs of [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu). Is that right? Could anyone whos synaptic works see if their repos point there as well?[/QUOTE]
Remove the "us." and try the standard repos.

---

### Post by sedgie on 2006-01-13
Well, I followed the directions here: 

[http://ubuntuforums.org/showthread.php?t=113334](http://ubuntuforums.org/showthread.php?t=113334)

and here:

[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

and the 404 error is gone. Now I have a "Temporary error resolving "[my school's proxy server here]"

---

### Post by wanger123 on 2006-01-13
Here is what I had to do for apt-get (synaptic) to connect to the outside world from my Uni's proxy

Add this to etc/bash.bashrc file: 
```
export http_proxy=“http://username:password@proxy.com:8080”
export http_proxy=“http://username:password@proxy.com:8080”
export http_proxy=“http://username:password@proxy.com:8080”
```

Then create /etc/apt/apt.conf file and add this to it (exactly as laid out here): 
```
Acquire
{
	http
	{
	Proxy “http://user:psw@proxy:port”
	};
};	
```

To see it: $echo $http_proxy or  $echo $https_proxy or $echo $ftp_proxy

For temporary session settings do this: 

```
$export http_proxy=http://user:psw@server:port 
$export https_proxy=http://user:psw@server:port
$export ftp_proxy=http://user:psw@server:port
```

cheers
wanger

---

