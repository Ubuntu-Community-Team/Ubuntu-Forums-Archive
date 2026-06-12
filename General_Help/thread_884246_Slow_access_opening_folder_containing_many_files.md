---
title: "Slow access opening folder containing many files"
date: 2008-08-08
forum: General Help
---

### Post by AnomalyDetected on 2008-08-08
One of the systems I use takes images from multiple cameras and stores many small jpg (about 20K each) inside a different folder for each day. These folder end up with hundreds to thousands of small files in them.

The problem I have is that Nautilus (2.22.3) is EXTREMELY SLOW is just OPENING the folder. I'm not even performing file operations yet, just trying to see what files are there.

On an Intel Pentium4 2.0Ghz platform with 512MB of ram, It can literally take an hour just to wait for all the files to populate when trying to view the folder. During the time, the CPU spikes to 100% and my RAM keeps creeping up until it is almost full, with scattered disk activity the whole while.

Something is wrong here. I just want to be able to browse through these and select the handful that I want to actually view.

Is it maybe trying to create thumbnails of each or something? Is there a way to disable that?

---

### Post by AnomalyDetected on 2008-08-08
Answered part of my own question while I was typing it. Evidently it WAS trying to create thumbnails for the thousands of files, which naturally was quite a chore.

I set this to "never" in the preferences menu of Nautilus, and now it is much quicker to view the folder contents, though still not as fast as I'd like. It's down to a minute or so instead of a full hour.

However, now I notice a huge delay in OPENING one of the many files. CPU stopped spiking, but huge disk activity for several minutes before it actually opens the tiny jpeg.

Why is it taking so long to "find" and load even just one of these files? EXT3 shouldn't fragment much from my understanding, so that shouldn't be an issue...

---

