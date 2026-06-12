---
title: "Firefox file upload dialog freezing"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Rangi01 on 2009-03-05
Hope I have posted this in the right place!

We have a problem that in firefox when we try to upload a file i.e. in GMail if we try and add an attachment to an email, the file upload dialog freezes.  Sometimes it freezes and is blank sometimes it gets as far as listing the files but that's it.

I believe this has happened since the last update we ran.  I have made sure that there are no new updates available.

This only appears to be happening on our Dell GX150 machines as my NEC Laptop is performing perfectly.

We are using Intrepid 8.10

We use the machines for work and it is important that we are able to upload files.  At the moment we have installed Opera as a work around and that performs the upload function fine but we would like to continue to use Firefox as we find it more user friendly.

Thanks for your help in advance.

Shane

---

### Post by martrn on 2009-03-05
You could reinstall firefox to see if that fixes the problem.

try:
----
Open up a terminal and type:

```
sudo apt-get update
sudo apt-get remove --purge firefox
```

then:

```
sudo apt-get install firefox
```

to first remove then re-install firefox.


If firefox still crashes you could install firefox2 see [http://thilinamb.wordpress.com/2008/12/18/how-to-switch-back-to-mozilla-firefox-2-in-ubuntu-810/]("http://thilinamb.wordpress.com/2008/12/18/how-to-switch-back-to-mozilla-firefox-2-in-ubuntu-810/") for how to do this.

---

### Post by Rangi01 on 2009-03-05
Thanks Martrn,

Removing and then reinstalling Firefox 3 did not help but your link to dual installation with Firefox 2 worked great.  Only issue I had was that there was no Key for FF2.  I solved it by running the following lines

# gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 0C5A2783
# gpg --armor --export 0C5A2783 | apt-key add -
# apt-get update

(found thanks to Google:) )

I have my machine up and running just 9 more to go!

Cheers

Shane

---

### Post by Rangi01 on 2009-03-10
Ok the problem turned out to be in the Add-ons.

We run Ubuntu 8.10 on Dell GX-150 machines.

Recently after doing a system update our file upload dialog box would just hang.  This was not only in GMail but also other programmes.

While trying to sort the issue another lot of updates came through and after loading them it was only GMail that would hang so I decided it must be an Add-on that was causing the problem.

We have Speed-dial and Better Gmail 2 so I un-installed both of these and then re-installed and hey presto everything works as it should.

Hope that this helps somebody out there.

Shane

---

