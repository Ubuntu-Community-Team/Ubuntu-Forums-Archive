---
title: "convert SPSS 8 database to something that I can use in Ubuntu"
date: 2008-09-29
forum: General Help
---

### Post by pytheas22 on 2008-09-29
I have an old SPSS version 8 database that I need to access on Linux (at least to read, but ideally to modify as well).  I know that I can buy SPSS for Linux, but I don't want to do that if possible (I'm also not sure how well the modern version of SPSS, version 16, would work with this database, which was probably made sometime in the '80s).

My ideal solution would be to find a free program with similar functionality to SPSS that would run on Linux, and convert my database to be compatible with that new program.  Failing that, I would like to find a way to at least open the SPSS database on Ubuntu to read the contents.  gedit won't open it, and if I cat it from the command-line, it's all just gibberish.

I am also interested in finding a good free database program oriented towards the social sciences.  If anyone can give recommendations, I would be happy to hear them.  I haven't really worked with database software in the past and therefore am not really familiar with the options on any operating system, but I need to start building some databases for history projects, and I would prefer to do that using free software if at all possible.

Thanks in advance for any suggestions.

---

### Post by cariboo on 2008-09-30
If I remember properly I think that Spss was just a comma delimited flat file db back then. If you can open it with a text editor you should be able to convert it for use in mysql.

Jim

---

### Post by shaggy999 on 2008-09-30
Check out 'pspp' and 'r-cran-foreign'. The latter is an addon package for "GNU R" (located in package 'r-base-core') which allows GNU R to read a multitude of data files, including spss files. pspp is like an open-source spss (notice the reversal of p's and s's)_and GNU R is a 'statistical computing language'.

All are in the repos.

---

### Post by pytheas22 on 2008-10-01
Thanks so much for both of your answers.  I was quite delighted to find pspp, which seems to offer most of the features of spss, with the exception of costing an inordinate amount of money.  Once again, free software saves the day.  I can't seem to get pspp version 0.6 (the only one with a GUI) to work in Hardy, but it works in Intrepid, so perhaps I'll just have to switch over earlier than planned.

I have one follow-up question, however: do you know of any binaries for pspp compiled for OS X?  Part of the deal for me to have access to the spss database that I need to open was that I also figure out a way for a professor to run it on his Mac, ideally without purchasing anything.  It seems that pspp will run on a Mac, but you have to compile from source, which I doubt he'd be able to do (and he's on the other side of the country, so I can't do it for him).  Are there any pre-compiled binaries of pspp anywhere that will run on an (Intel) Mac?

Thanks again for the help.

---

