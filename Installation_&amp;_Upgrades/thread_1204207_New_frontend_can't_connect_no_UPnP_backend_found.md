---
title: "New frontend can't connect no UPnP backend found"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by trevs.bronco on 2009-07-04
Hi All,

I built a new front end using a Zotac IONITX. I had a hard time getting the software on the machine as there is no optical drive. tried to load from USB flash, couldn't get that to work, tried borrowing the optical drive from my backend machine, no luck there either so I ended up putting the HD from the front end into the backend and installing it there.

At first I would get a screen asking for language then the "No UPnP Backends found" box I click ok and get the configure screen, all information is correctly entered from the Mysql.txt file on master backend. hit next hit finish and get a cannot find (ping) host on the network and then back to the configure screen. I used to be able to hit cancel here and the frontend would start, I would be able to watch tv and recordings but not videos or music. now I can't even do this, I cannot get the front end to start at all. The only changes I made in set up between being able to have a limited front end and no frontend is I made the IP addresses static.

TIA,
Trev

---

### Post by issih on 2009-07-04
Hmmn..bit confused here.. there are various things that are needed to allow remote front ends to work.

1) static ip for backend machine (not 127.0.0.1, a real ip address obviously)

2) in general options of backend setup set the local backend and master backend ip address to the static ip of the backend box on the local network.

3) enable remote access to the mysql database (this is easy from mythbuntu control centres services tab)

4) enter the appropriate details in the remote frontend and things should then work.

You certainly need to be able to ping the backend box from the frontend using the static  ip.

until you can do that in a terminal you stand no chance.

hope that helps

---

### Post by trevs.bronco on 2009-07-04
> **issih said:**
> Hmmn..bit confused here.. there are various things that are needed to allow remote front ends to work.

1) static ip for backend machine (not 127.0.0.1, a real ip address obviously)

2) in general options of backend setup set the local backend and master backend ip address to the static ip of the backend box on the local network.

3) enable remote access to the mysql database (this is easy from mythbuntu control centres services tab)

4) enter the appropriate details in the remote frontend and things should then work.

You certainly need to be able to ping the backend box from the frontend using the static  ip.

until you can do that in a terminal you stand no chance.

hope that helps


1. done

2. no local backend

3. Done

4. info entered 
   can ping backend from terminal

---

### Post by trevs.bronco on 2009-07-05
anyone have any ideas here? I definitely have connection between the two machines i have NFS setup and can open files on the backend. I did however notice that the file shares failed to mount on startup. could that be a clue to my problem?

thanks in advance

Trev

---

### Post by issih on 2009-07-07
Your reply for no 2 does not make sense.

You HAVE to have a backend somewhere. On the machine where the backend is you need to run the backend setup and in the general options section set both the "local backend" address and the "master backend" ip addresses (those are the names myth uses) to the static ip address of the machine running the backend on it.

if that isn't happening you will need to troubleshoot bit by bit...check that a frontend running on the same machine as the backend works, then check the logs on the various machines to see if any useful titbits are hiding in there:

the logs are in:

/var/log/mythtv

If you have network connectivity, and your backend address is static, then really its down to a myth tv config issue, or possibly a borked mysql database.

---

### Post by NinjaNumberNine on 2009-07-13
I have a similar problem [[COLOR=Red]**here.**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1211669")

Mine has better documentation maybe.

---

### Post by NinjaNumberNine on 2009-07-13
Whoohoo! I fixed mine by reading all of these posts, Thanks!

---

