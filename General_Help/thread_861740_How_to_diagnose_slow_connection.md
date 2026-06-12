---
title: "How to diagnose slow connection"
date: 2008-07-16
forum: General Help
---

### Post by sofasurfer on 2008-07-16
For the last 3 days my internet connection seens to be faulty. Downloads take forever. Speed comes and goes. The last straw was today when I could not perform a 'sudo apt-get update' because the process appeared to stall off and on, but mostly stall.

I really do not know if the problem is my computer or if it is the fault of the internet or my server. 
How would I learn where the fault lies?

---

### Post by drs305 on 2008-07-16
As far as updates to ubuntu, you can go to synaptic, settings, repositories. Click on the 'download from' window, select 'other' and then 'select best server'. It will check the speeds of the different mirrors and provide a suggestion as to which one would be best at that time.

It will not help if it is your provider or a system problem - only if your selected ubuntu mirror is slow for some reason.

---

### Post by dislocated on 2008-07-16
Are you wireless or plugged in?

My wireless has slowed down from time to time and I often find the problem to be an overcrowded channel.

---

### Post by sofasurfer on 2008-07-16
I'm wireless. Running off a wireless router. Sometimes when the internet is busy it slows me down. But it never lasts for days like this. And I get surges of speed sometimes. It makes me feel that it may be a problem with my pc or something there abouts. I will hard wire my connection after work tonight and see if anything changes.

---

### Post by sofasurfer on 2008-07-17
I found the problem. My antenna on the back of my router was not pointing straight up. It was at about a 45 degree angle. Pointing it straight up give a very fast internet connection. At a 45 degree angle the connection is about non-existant. I don't know why I have never noticed this before. I have never before paid a lot of attention to that little 3 inch antenna.

---

### Post by sofasurfer on 2008-07-18
I spoke too soon. I swear that moving my antenna DID make a differance. But that only lasted a few minutes.

Heres my current status. With a wired internet connection there is no problem. But with wireless the connection is stalled.

With the pc in the same room as the router I will get messages that data is being transferred and connections have been made. Sometimes the page will load after a few minutes and more often than not, I give up waiting for it. 

Now if I take the pc to the other room, on the other side of the wall from the router, and only about 6 feet away, the web pages always time out. There is no connection.

This problem started a few days ago. Until then I had a good internet connection.

Did my wireless adapter go bad?

Where do I begin?

---

### Post by dislocated on 2008-07-18
It really sounds like the problem I had with an overcrowded channel.

You might want to try this:

Open your router setup page in your browser. In the wireless setup section you should see an option to select channels 1 through 11. Most routers will default to channel 1 out of the box. So if you have a lot of neighbours all on channel 1, then you are better off on channel 8 or something. Play around with it and see if it helps.

It worked for me, at any rate.

---

### Post by sofasurfer on 2008-07-18
The channel was my problem. I asked about this in another thread and was told to change channel. My connection is still slower than it should be I think (always has been) and so now I will try other channels to see if it helps more than it has so far.
I'll appreciate any info you have on helping to improve signal strength. 
Thanks.

---

