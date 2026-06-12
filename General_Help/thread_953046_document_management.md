---
title: "document management"
date: 2008-10-19
forum: General Help
---

### Post by Zyphrexi on 2008-10-19
I write. A lot. And I have probably hundreds of randomly named text files, images, etc. I use tomboy like crazy. I need to find and organize this stuff so it's more streamlined than helter-skelter. It's hard to backup what you can't find.

I tried Incollecter, but found it difficult to use. Any suggestions?

---

### Post by Sam on 2008-10-19
Do you use tracker (search tool) ? It indexes the content of the files in real time and you can find a document by searching a word contained inside.

---

### Post by forger on 2008-10-19
1) Applications > Accessories > Tracker search tool ?
2) perhaps the command line find?
```
find $HOME -depth -name "*a*.doc"
find $HOME -depth -name "*some*.png"
find $HOME -depth -name "cool*.txt"
```

I would suggest organizing by dates as folder names as "YEARMONTHDAY" i.e. "20081003" :)
A program that tags various files would be useful, something like gmail's labels, never found one though
Edit: Looks like tracker-utils has a solution for tagging:
> NAME
       tracker-tag - command line tool for setting and searching tags/keywords

SYNOPSIS
       tracker-tag [options] FILE...

DESCRIPTION
       tracker-tag  allows  you  to  modify  the  tags  that  are  associated with a file.  The actual information is stored in a tracker
       database.

OPTIONS
       -?, --help
              Show summary of options.

       -a, --add=TAG
              Add specified tag to a file.

       -r, --remove=TAG
              Remove specified tag from a file.

       -R, --remove-all
              Remove all tags associated with a file.

       -l, --list
              List all tags associated with a file.
              If no file name is given, all known tags and their count is listed.

       -s, --search=TAG
              Search for files matching the given tag.


---

### Post by Zyphrexi on 2008-10-19
I was kind of hoping for something to help me organize it all.

I have so much junk it's ridiculous. I thought about something like tracker (replacement for beagle?) but there's no telling what folder the file i'm looking for is in.

---

### Post by Sam on 2008-10-19
What about:
```
locate <filename>
```


If you wish to update the locate database:
```
sudo updatedb
```

---

### Post by Zyphrexi on 2008-10-19
I know about stuff like that. I guess i'm having trouble explaining.

I guess I'm thinking more in terms of a front-end. locate/slocate/mlocate is good when you have an idea what the filename is and you need the pathing.

---

### Post by jflaker on 2008-10-19
You could try this

[http://www.epiware.com/](http://www.epiware.com/)

I haven't tried it, but Google "Open Source Document Management"  There are plenty of solutions, some overkill and some just not functional at all.

---

### Post by forger on 2008-10-19
> **Zyphrexi said:**
> I was kind of hoping for something to help me organize it all.

I have so much junk it's ridiculous. I thought about something like tracker (replacement for beagle?) but there's no telling what folder the file i'm looking for is in.

By default, tracker indexes and searches your text files and documents, even within their text. Feed the tracker a search text string, something that you believe is unique for the text you're looking for. Then hit enter and let it do its magic :)

The folder was a recommendation on how to start categorizing them *from now on*. One by one, day by day, you get the job done without even noticing :)

---

### Post by adventurer on 2009-01-08
There are two document managers in Synaptic.  Both Apache and PHP based.  I have no experience of either of them.

---

