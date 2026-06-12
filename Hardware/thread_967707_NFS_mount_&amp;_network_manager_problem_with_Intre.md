---
title: "NFS mount &amp; network manager problem with Intrepid"
date: 2008-11-02
forum: Hardware
---

### Post by neorg on 2008-11-02
I am running Intrepid now for about 3 weeks, It's really GREAT!!! There are still some small thinks to fix.

One of the problem I have is that de NFS mount over wifi won't succeed. After a login the network manager is not ready jet so mount can't succeed at that moment. This has to do with the startup sequence from mount an the network manager in Gnome. 

The NFS mount can only succeed after that the wireless connection is up and running and the host reachable. 

The solution I created is a script that is started by sessions (System -> Preferences -> Session). The script has a loop that test 10 times if the host where i want to connect to is reachable. If it (finally) is, than it mounts my NFS shares.

In fact this is a solution for [_this **closed** tread NFS mount with Intrepid_]("http://ubuntuforums.org/showthread.php?t=943249")

A assume that you have the right mount lines and options in your /etc/fstab. 

Something like:
```
#NFS mount to [COLOR="Red"]HOST[/COLOR]
myhost:/extra /extra              nfs rw,user,rsize=8192,wsize=8192,timeo=14,intr,bg

myhost:/home/[COLOR="Red"]USER[/COLOR] /home/[COLOR="Red"]USER[/COLOR]/[COLOR="Red"]HOST[/COLOR] nfs rw,user,rsize=8192,wsize=8192,timeo=14,intr,bg

```

I also assume that you have the right export on your hostmachine in /etc/exports.
Something like:
```
/homer/[COLOR="Red"]USER[/COLOR]       *.LOCAL.DOMAIN(rw,root_squash,sync,no_subtree_check)
/extra          *.LOCAL.DOMAIN(rw,root_squash,sync,no_subtree_check)
```


Be sure that you have made the directories where to mount to. IN this case **/extra** and **/home/[COLOR="Red"]USER[/COLOR]/[COLOR="Red"]HOST[/COLOR]**

Here is the script.

Save it on a place in your home environment.
Lets say /home/[COLOR="Red"]USER[/COLOR]/bin/mount.[COLOR="Red"]HOST[/COLOR].sh 

[SIZE="2"]
note:
- Replace [COLOR="Red"]HOST[/COLOR] with the hostname of the machine you want to connect to.
- Replace [COLOR="Red"]USER[/COLOR] with your username
- Replace [COLOR="Red"]LOCAL.DOMAIN[/COLOR] with your local domain name[/SIZE] 

```
#!/bin/bash

# This script mount the partitions or directories from machine
# HOST on you wifi laptop. Because of the fact that in Intrepid
# the network manager start so late that it's  
# to late for a normal mount at boot.


# Number of times we are goning to try is we can ping the host.
COUNTER=10

# A loop
while [ $COUNTER -gt  0 ]
do
 # Ping the host (HOST in this case)	
 ping -c 5 [COLOR="Red"]HOST[/COLOR]

 # See is we got a "0" as result from the ping command.
 if [[ $? != 0 ]]; then
	 # If it is 0 than it's not OK. 
	date '+%Y-%m-%d %H:%M:%S Connection Unavailable'
 else
	# If we got something other than 0 than the host is reachable
	# let's mount the thinks we want	
	mount /extra
	mount /home/[COLOR="Red"]USER[/COLOR]/[COLOR="Red"]HOST[/COLOR]

	# set counter to zero to quit the while loop	
	let COUNTER=0 
 fi

 # Subtract one from the counter so the number
 # of times the while loop has to go is one less
 let COUNTER=COUNTER-1

done

```


Make the script executable: 
[/CODE]chmod 755 mount.[COLOR="Red"]HOST[/COLOR].sh[/CODE]


Add a entry in your start up session (System -> Preferences -> Session)

[/CODE]sh /home/[COLOR="Red"]USER[/COLOR]/bin/mount.[COLOR="Red"]HOST[/COLOR].sh [/CODE]

Now  your NFS mount will come up automatically after login.

---

