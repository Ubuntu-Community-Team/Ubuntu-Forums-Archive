---
title: "Parsing links in Emails"
date: 2008-11-14
forum: General Help
---

### Post by munkymac on 2008-11-14
I have kind of an odd request. I get a ton of emails every day with links to mp3s hosted (I'm in the music business). Because of this, I set up a filter in Thunderbird that searches the body of the email for ".mp3" and dumps it straight into my mp3 subfolder of my inbox.

I'm trying to find a program (or two separate programs) that can do the following: Parse out the links in the emails that end in .mp3 and either 
[INDENT]a)download them to a specified folder, or
b)output them to a text file that i can then use in a second program to download the files[/INDENT]

I'm guessing if all else fails, a script could be run in the terminal that would do option B, but I thought i'd see if there was something already out there (and i dont know how to write any scripts, to be honest)

any ideas?

PS- if someone could point me to a "script writing for dummies" tutorial, that might work too.

---

### Post by spibou on 2008-11-14
I'll handle b)
```
awk '{for (a=1 ; a <= NF ; a++) if ( $a ~ /\.mp3$/ ) print $a }' your-email-file > list-of-links
```
My impression is that recognising links is a hard problem to solve in full generality. Do the links you get contain www? Do they contain http?

Note that the list-of-links file gets overwritten every time you run the script. If you don't want that replace > with >>

Task a) is also easy to handle but I'm not sure under what name you would want the files to be saved. My main worry is that a new mp3 may overwrite the file for an old mp3. With that caveat here's an effort:
```
 while read a ; do wget "$a" ; done < list-of-links
```
Run it when you are in your mp3s directory. wget will automatically choose a file name under which it will save the link but it's possible that the file it chooses already exists; unlikely I think but cannot be ruled out.

---

### Post by ProgramErgoSum on 2008-11-14
Would receiving links to mp3 *in an email* would be the only choice ?

---

### Post by munkymac on 2008-11-18
> **spibou said:**
> 
Run it when you are in your mp3s directory. wget will automatically choose a file name under which it will save the link but it's possible that the file it chooses already exists; unlikely I think but cannot be ruled out.

Spibou, this is awesome. Here's some of the results when I ran it:

Part A: A few of the links in the text file were incomplete. Some were missing just the [http://,](http://,) while others were missing chunks of the address. Approx. 95% of the links were perfectly formed. for some reason (I'm assuming it's because of the html in each email itself) there were a few whose links I can mouse over in my email program (Thunderbird) and it will show the link, but the links did not show up in the readout. Again, this was about 5-10% of the overall total.

Part B: any duplicates were downloaded with the following name convention:

sample.mp3
sample.mp3.1
sample.mp3.2
sample.mp3.3

It ended up being really easy to deal with, because all I had to do was run a search in the folder for files with ".mp3." in their name, and all of the duplicates popped up so I could delete them.

Then I just used EasyTag to scan the ID3 tags and rename the files like I wanted them, and I was done. It was breathtakingly easy, and the margin of error was small enough that I will be using this a whole lot.

Question: my business partner uses a Mac. Since it is the same basic underlying UNIX framework, will he be able to run these terminal commands on his MacBook and achieve the same result?

---

