---
title: "faster updates via concurrent downloads"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by Nekomusume on 2008-12-19
So, as it stands, when updating ubuntu makes a list of all the various files it needs to download, and then downloads them one at a time, in order, regardless of available bandwith, download speed, etc.

Is there a way to make it download multiple files at once? Given that the top speed I've seen out of any single connection is 15KB/sec, with most being considerably lower than that, concurrent downloading of files would take a lot of the aggravation out of larger updates/installations - such as the one you do right after installing the OS.

If not... why not? This is stupidly inefficient.

---

### Post by kostkon on 2008-12-19
> **Nekomusume said:**
> So, as it stands, when updating ubuntu makes a list of all the various files it needs to download, and then downloads them one at a time, in order, regardless of available bandwith, download speed, etc.

Is there a way to make it download multiple files at once? Given that the top speed I've seen out of any single connection is 15KB/sec, with most being considerably lower than that, concurrent downloading of files would take a lot of the aggravation out of larger updates/installations - such as the one you do right after installing the OS.

If not... why not? This is stupidly inefficient.
You could change the server that you are using (in *System &#8594; Administration &#8594; Software Sources*).

Also, check the option of using *apt-p2p*, although I don't know how well it works.

---

### Post by jenkinbr on 2008-12-19
If you use synaptic, you can generate a download script and then modify it so that it is just a list of URLs.  Then, use a download manager that supports concurrent downloads to download the packages.  Then, you can either drop these into apt's cache directory and use apt or synaptic to install them, or you can navigate to the directory where you saved them and issue ```
sudo dpkg -i ./*.deb
``` followed by ```
sudo apt-get install -f
``` just to be safe.

---

### Post by zika on 2008-12-19
there is an interesting thing I noticed a while ago. on my 32-bit machines Intrepid update manager downloads several files concurrently while on 64-bit machines it doesn't. what's going on? BTW torrent (apt-p2p) works OK.

---

### Post by markbuntu on 2008-12-19
I saw the opposite. 32 bit downloaded serially while 64 bit downloaded concurrently. But I have not seen it do that for a while now, probably some update "fixed" it.

---

### Post by Nekomusume on 2008-12-23
> **zika said:**
> there is an interesting thing I noticed a while ago. on my 32-bit machines Intrepid update manager downloads several files concurrently while on 64-bit machines it doesn't. what's going on? BTW torrent (apt-p2p) works OK.

You wouldn't happen to have nice simple directions for installing apt-p2p, would you? It doesn't seem to be available via the manager, and the directions I've found online weren't exactly user-friendly.

---

### Post by zika on 2008-12-23
> **Nekomusume said:**
> You wouldn't happen to have nice simple directions for installing apt-p2p, would you? It doesn't seem to be available via the manager, and the directions I've found online weren't exactly user-friendly.

I've used [http://www.ubuntu-unleashed.com/2008/11/howto-update-to-ubuntu-intrepid-ibex.html](http://www.ubuntu-unleashed.com/2008/11/howto-update-to-ubuntu-intrepid-ibex.html) . It worked like a charm. Beware that Your speed might not be as it were when using direct link. But the installation itself was strighforward. Have fun.

Also I've found that [http://ubuntuforums.org/showthread.php?t=962741&highlight=p2p+update+manager](http://ubuntuforums.org/showthread.php?t=962741&highlight=p2p+update+manager) works great.

These days I see a lot of outbound traffic on my computer that I link with apt-p2p and I would like to turn it off for some time. What is the right way to do it?

---

