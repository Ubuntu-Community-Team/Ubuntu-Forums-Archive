---
title: "Would LOVE to Automatically track numb. of pages sent to printer since new toner?"
date: 2015-04-18
forum: Hardware
---

### Post by harelb on 2015-04-18
Hi,

I originally also wanted to find out how to [override]("http://ubuntuforums.org/showthread.php?t=2272235&p=13263035#post13263035") my first laserprinter blocking me from printing to see if the "low toner" is in error...but no one posted a reply how to override.

I did have a second question in that same post I'm hoping is doable - is there a utility in ubuntu where I can (after telling it to "reset to zero" when I put in a new toner cartridge) that it automatically keeps track of "number of pages" (counting twice when doign two sided printing...and for simplicity, assume all pages are in draft/toner safe mode) printed to date?

This will a) help estimate "how many pages left before new 'low toner' error" 

and

b) it will help us bust false claims, if any exist, by companies who claim 700 pages but routinely give 400 for example

I'd LOVE a utility that does that...help anyone?

---

### Post by kostkon on 2015-04-18
The easy way would be the following:

You could make a note of the first page after putting the new toner and the last page before it ran out and then check your Print Queue either by clicking on the printer icon in the tray, if it is visible or by opening your printer settings window and right-clicking on the printer's icon (make sure you click the green tick icon to show the completed jobs in the Print Queue window.)

You can hopefully then subtract the id of the last print job from the first one to calculate the number of pages. If the ids are arbitrary then you'll obviously have to manually count them yourself.

Hope that helps somehow.

---

### Post by harelb on 2015-04-18
Kostkon, definitely, if it does turn out to be sequential and not "arbitrary" as you put it, then definitely would help.

Trying to figure out what this tray is...On my system 12.04.5 LTS, I go to top left icon (is that the "tray"? steps differ somewhat from what you mentioned) then System Tools. Then I select System Settings from submenu. In there, I select Printers. 

There it lets me select which of two (old inkjet I am now back to, and the laserprinter) It lets me select "jobs" (and displays two old ones but no left or right click lets me kill them, but that's another subject) iets me also select Options, and "Print Test Page" 

Don't see where I can get any response by right-clicking.. Options does not seem to be same as the Settings you mentioned so am I in the wrong place? I would have thought that going to System Settings and then Printers would let me (from there) reach anywhere relevant to printer, but now I'm still fiddling with it and not yet finding the place to right click to see ID numbers for what's been printed..

---

### Post by cariboo on 2015-04-19
You can use the CUPS interface on the computer you have the printers connected to, to see some of the info you want. To access the interface on the computer the printers are connected to, open a web browser and type the following command:

```
http://localhost:631
```

Click the administration tab and you should see something like in the screen shots

---

### Post by harelb on 2015-04-21
Thank you cariboo, this url does work for me, and I can see the Jobs and Printers and Administration etc just like your screen shots.  Now I just need a bit more clarification of the steps involved.

Let's say that tomorrow I put in the new Toner (I reverted to my Inkjet and I'm managing with before it runs out of ink..but would be nice to get back to laserprinter) What exactly do I do, step by step? I mean, under "Jobs" I do see a couple of jobs, and those have a left hand column that gives ID numbers:

DCP7060D-1201 

and

Officejet-4300-series-1207 

which are two jobs that somehow got stuck. Never mind those jobs, I'm not worried about losing those print jobs, I'm just trying to understand the process exactly, step by step...These job ID numbers seem to be sequential, but, do they only appear for jobs that are either "in the middle of being sent to the printer" or else that got "stuck"?

If I put in the new toner tomorrow, do I need to rush to reload my browser tab with [http://localhost:631](http://localhost:631) ? Otherwise, where would the ID numbers appear, is what's not clear to me, since the only place I see ID numbers for any job, is the above, for jobs that got stuck, but if my first page sent to printer is not "stuck" then where, exactly, would I find it's ID number?

If you could clarify that, then yes, that would be helpful, I would record that number for the first page, and then I'd look at the ID when I get "low toner" message, and subtract... (though it still looks like the ID increases by 1 for each job, not for each page, but  I'm not 100% sure, and this is at least a start...)

S

---

### Post by kostkon on 2015-04-21
> **harelb said:**
> Thank you cariboo, this url does work for me, and I can see the Jobs and Printers and Administration etc just like your screen shots.  Now I just need a bit more clarification of the steps involved.

Let's say that tomorrow I put in the new Toner (I reverted to my Inkjet and I'm managing with before it runs out of ink..but would be nice to get back to laserprinter) What exactly do I do, step by step? I mean, under "Jobs" I do see a couple of jobs, and those have a left hand column that gives ID numbers:

DCP7060D-1201 

and

Officejet-4300-series-1207 

which are two jobs that somehow got stuck. Never mind those jobs, I'm not worried about losing those print jobs, I'm just trying to understand the process exactly, step by step...These job ID numbers seem to be sequential, but, do they only appear for jobs that are either "in the middle of being sent to the printer" or else that got "stuck"?

If I put in the new toner tomorrow, do I need to rush to reload my browser tab with [http://localhost:631](http://localhost:631) ? Otherwise, where would the ID numbers appear, is what's not clear to me, since the only place I see ID numbers for any job, is the above, for jobs that got stuck, but if my first page sent to printer is not "stuck" then where, exactly, would I find it's ID number?

If you could clarify that, then yes, that would be helpful, I would record that number for the first page, and then I'd look at the ID when I get "low toner" message, and subtract... (though it still looks like the ID increases by 1 for each job, not for each page, but  I'm not 100% sure, and this is at least a start...)

S
If you click on Completed Jobs you'll see all the jobs that have been printed off.

Many printers provide a way to print out on a page some basic information about them, like the printer's Product Id, date of manufacture, model no., ink status, and among others the number of pages printed so far by pressing a specific combination of keys on the printer. I know that my old HP printer (DeskJet 840C, from the 90's) has one. I'm sure your HP printer has one as well but you'll probably need to use your Google-fu on this one.

Since your printer happens to be from HP, you can install the HPLIP GUI utilities package (search for it in the Software Centre). That package provides the HPLIP Device Manager utility which is the de-facto GUI utility for configuring and setting-up HP Printers; you might be able to get all the above information from that instead.

---

### Post by harelb on 2015-04-22
"Completed jobs" did it :-) Well that plus a little more than 5 minutes of patient adding up...

Unfortunately you can't subtract ID numbers since those increment up by 1 for each job, not for each page...but 90%+ of my jobs are 1 page, so other than "EndID-STartID+1" I manually added...if one page of 100 jobs is all 1 pagers except for a 5, 2, 2, 2, 4, 3, and 4 page jobs, just add another 4+1+1+1+3+2+3 additional pages for that range, etc. Do that from start until end, about 5 pages and the answer is...

drumroll...

The answer is they didn't fib by as much as I thought...but are still bending the truth...Total number of pages: 651 (job ID 701 was first, until 2108, plus additions for multi-page jobs, minus two cancelled jobs)

Keep in mind they not only give an estimate of "700 pages" on the box but that I put the thing into toner-saver-mode on **day one**....God help you if you had not done that...and even doing it on day 1, still almost 10% below their advertised number...

Though as I say, not as bad as I thought...So I used my google-fu to find out what the heck google-fu means...and found out...I think things are fu-bar here, frankly. What I mean is, why should we in 2015 have to google anything, on these two levels I hinted about at the outset:

_1. On the individual level _- why not have it built into ubuntu, no needing to google for anything on the HP website, less control by HP, more control by user, less time wasted googling, just a dialog box under Printers...the limitation surely isn't a technical one. At HP's end of things, it's not technical, but to do with their control, their profits, etc, but at our ubuntu end, I don't see any technical reason we not implement this (if there is a technical reason due to info HP won't release, time for open source printer alternatives to HP!) 

_2. On the community leve_- who not simply have user-approved semi automated statistical gathering. This is the kind of thing that Pro Publica would do an expose about, well, not quite that big, but have semi automated statistical gathering from all ubuntu users who approve it, so we know from a sample of 100 or more users, what is the average number of pages that a toner cartridge from HP (or other manufacturer) lasts.

If this feature was in place, when I install the new toner, I'd get a dialog, saying, "do you agree to share stats on how long the previous one lasted? It was 651 pages" and I'd click "yes" and it would be sent to some .org server and once we have large enough a sample, publicize that, and compare with other printers from the same manufacturer, and compare to other manufacturers. 

Too ambitious you say? This is the second decade of the 21st century, quantum computing is "hard", but this? This stuff? This stuff should be easy. Not only that, it should be in place. If someone knows url for suggesting such projects, other than me just ranting about it here that is, let me know :-)

When I have more free time I'll look into HPLIP (I think folks know how to interpret the qualifier in the first half of this sentence ;-)  )No seriously,I might, it might be an easy google..but at least I know "651 even in super stingy toner saver mode the whole time" 

End of rant (or at least end of adventure finding out how many pages the toner that came with printer lasts for) for tonight :KS

---

