---
title: "Something like Yep?"
date: 2008-08-20
forum: General Help
---

### Post by richiethom on 2008-08-20
Hi

When I was on the Mac, I used a simple Document Management program called Yep, which is described as "iPhoto for PDFs". Basically you could scan documents into it and then give them tags so that the PDFs were easy to find. (full details here: [http://www.yepthat.com/yep/index.html](http://www.yepthat.com/yep/index.html))

I was wondering if anyone knew of a similar application for Ubuntu. I've seen jLibrary (written in Eclipse/Java) and a web-based solution, but both seem a bit over the top (Yep was brilliantly simple) for what I want. Perhaps Gnome supports this out of the box without me knowing?

Any suggestions or ideas?

Thanks in advance

Rich

---

### Post by amitkher on 2008-08-20
In general, linux developers will not be satisfied with such a simple feature set. PDF centric, that too you have to scan documents into it for it to work? Lame. Mac developers might generally glorify simplicity and may not see this as lame.

Desktop search engines: beagle, tracker etc. will let you search many types of files. To make them mimic your limited requirements, do this. Instead of "scanning" PDFs into it, save your PDFs in a fixed directory that is used for this purpose. Limit tracker/beagle to only index this directory so that they do not start indexing your whole system.

You can also limit them to index only PDFs, but then they will search a large portion of your hard disk looking for PDFs whenever your PC is idle. This is wasteful of energy and effort.

---

### Post by richiethom on 2008-08-20
Lame it may be, but it worked for me. I don't know Tracker and Beagle that well, and  haven't got on that well with Tracker in the past - I will give Beagle a go.

Is there a mechanism for tagging files that Beagle can use? Without tags, for scanned PDFs without OCRing them (which I don't really want to do), there's not going to be much content to index.

---

### Post by amitkher on 2008-08-20
Lame? I was giving you the point of view of typical open source developers. If you need this, it is definitely not lame for you.

I don't know about tagging, you could suffix your tags to the filename when you copy it to the specific directory. In this case, even if the PDF cannot be indexed (e.g. when it is password protected) you will be able to search using at least your tags. E.g. a PDF about Ubuntu forums that is named random.pdf. When you copy it to your special directory, just name it random:ubuntu:forum:linux:help.pdf (where ubuntu, forum, linux, and help are your "tags").

OCR? Are your PDFs "protected"? When you press ctrl-f in adobe acrobat reader, can you not search for text? Unless the supplier of the PDF thinks you are a criminal, he will give you a PDF that is quite searchable and indexable. Of course, if it is mainly images, there is not much to search as these search engines do not search images.

Generally people have bad experience with tracker and beagle because the task of these search engines is herculean. Index ALL your user files, not only in your home directory but all the places where people generally keep their files. Considering the current state of storage technology (hard disk, flash etc.) this is a huge task. Hence the search engines spend a lot of time indexing, lowering the performance of the computer a lot. They also use a lot of power, reducing battery life if a laptop.

Your task is simple. Remember to restrict them to this directory, and you will not even notice the strain on your system. If you rely on only the "tags" that you suffixed to filename and forbid tracker/beagle to index contents of the files, it will be trivially simple task to perform even for a huge number of PDF files.

---

### Post by richiethom on 2008-08-20
Sorry, I think I've not been very clear :)

I will be scanning in things like phone/utility bills, and would like to be able to add tags such as "utility", "water" etc. Therefore the only metadata there will be will be the tags...I will have a go and see how I get on.

Maybe I should write one!

---

### Post by amitkher on 2008-08-20
Then I think you could try my solution. Highly likely to work.

---

### Post by richiethom on 2008-08-20
Thanks for your help - I'll give it a go!

---

