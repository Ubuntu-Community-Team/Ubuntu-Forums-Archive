---
title: "Nautilus CD/DVD writing problem - bad filenames"
date: 2005-11-27
forum: General Help
---

### Post by justmehere on 2005-11-27
Hi I'm getting a message:

File image creation failed
Some files have invalid filenames.

when I try to write files to a CD/DVD.  

I have several thousand files in multiple directories. Has anyone got any tips for finding and renaming the culprits.

---

### Post by terotil on 2007-07-21
I had the same issue. After converting filenames (in my case from winlatin, aka cp1252) to utf-8 burning went fine. I did the conversion with convmv. Running 

[font=monospace]convmv --notest -f cp1252 -t utf-8 -r .[/font] 

in the directory containing the tree I was going to burn did the job.

---

