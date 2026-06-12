---
title: "Email &amp; spreadsheet (or database) help needed"
date: 2008-08-24
forum: General Help
---

### Post by stevemcb263 on 2008-08-24
I get a daily email that lists my investments by ticker ID and end of day value per share.  I'm using Thunderbird 2.0.0.16.

Manually copying this data from the email and posting into a spreadsheet to track the stock's progress has become tiresome, PLUS I need a project to help me learn.  I'm fairly new to Linux (I am using Ubuntu 8.04, if it makes any difference). 

I need ideas on how to get the emails to write as a file (automatically, I don't want to have to open each email and press Ctrl+S), and then get the data read into a spreadsheet (or a database).

I posted a question about automatically saving the emails on the T-Bird forums, but didn't get any responses.

Any creative solutions would be appreciated!

TIA,
Steve

---

### Post by Cheesehead on 2008-08-24
Can you receive the e-mail in any different format? Or, can you get the same information from a website? Or RSS feed? Those would be easier.

If not, you can do it with a script (bash or python - I suggest python)

Thunderbird needs filter option to pipe or run a program. If it doesn't, Evolution does.
Your spreadsheet needs to support supports XML or OpenOffice Calc files.


1) Your e-mail client needs to recognize the data e-mail and run the script on it.

2) Have a script to parse the e-mail and extract your data. This is not too hard - a week of learning python. This can also be done as a cron job parsing the data from a website or RSS feed.

3) Have the script open your spreadsheet file and put your new data in. This is harder because you need to understand how the spreadsheet file works - another week of learning python.

4) You open your spreadsheet normally, and -poof- all your data is there.

Of course, you cannot rearrange your spreadsheet or the e-mail format without breaking the script, unless you spend a third week of learning python to make the script very robust.

---

### Post by stevemcb263 on 2008-08-24
The data is available on the web, but I don't know how to automagically log into the website, navigate to the correct screen and capture the data I want from within an OpenOffice V2.4 spreadsheet.

Thunderbird does recognize the emails I receive right now, as right now it identifies the email on arrival and moves it to an alternate folder using a filter.  This is why it seemed to me it would be easiest just to export the email body text as a file in a particular directory/filename so I could use another program (like a stored procedure) to wait for the file to arrive and then parse the contents to get exactly what I needed.

From what I read on the Thunderbird website, there is currently no utility to automatically / individually save files as text based on message filters.  I have no idea where to even begin with writing an add-on for Thunderbird to 

I have no particular programming experience.   I did buy a couple of Python books, but learning is slow.  I am not at all opposed to learning (I would prefer to learn), but I need some direction on how to get started.

Thanks.

---

### Post by Cheesehead on 2008-08-24
My suggested steps for learning python for this project:
*Each is pretty easy - just an evening or two with the tutorial and you can make all the mistakes you want!*

Step 1: Write a 'Hello World!' script

Step 2: Write a script using the 'os' module to execute shell commands. Have the script ping [www.google.com](www.google.com) and tell you the result.

Step 3: (not python) Learn to Unzip and Zip an OpenOffice Calc spreadsheet - try to access and successfully change 'content.xml', and then make it a usable Calc document again. You can Google for instructions, or see my instructions at [http://kiwinc.itgo.com/ian/TechBlog.html](http://kiwinc.itgo.com/ian/TechBlog.html)

Step 4: Write a python script using the 'xml.elementTree.etree' module to open and parse the xml from a Calc file (just parse, that's all).

Step 5: Write a python script to unzip a spreadsheet, modify content.xml, and zip it back into a usable Calc document again.

Step 6: Write a python script that uses the 'regex' (regular expression) module to open your .bash_history file and tell you the 10 most used commands.

When you finish step 6, you will have all the tools you need to *anything* with Calc files, putting new data into them, and getting data out of them.


Tutorials: *There are lots, as you know. Don't get wrapped up in them too deeply - you're not trying to get a job doing this*
[http://www.python.org/doc/current/tut/tut.html](http://www.python.org/doc/current/tut/tut.html)
[http://diveintopython.org/](http://diveintopython.org/) and 

Reference: *I use this ALL the time to answer my questions*
[http://www.python.org/doc/current/lib/lib.html](http://www.python.org/doc/current/lib/lib.html)

---

### Post by Zill on 2008-08-24
stevemcb263:  I used to use web queries with Excel but have never tried them with OpenOffice Calc.  Take a look at this link...

[http://www.openofficetips.com/blog/archives/2004/11/webquery_scrapi.html]("http://www.openofficetips.com/blog/archives/2004/11/webquery_scrapi.html")

---

### Post by stevemcb263 on 2008-08-25
Zill,

Thanks!  I had been looking for similar instructions but had not been able to find them.

I got feedback from MoneyCentral (in response to the query I set up) that they didn't allow automated queries (Ooops!)  I guess I queried them too many times when I was trying to get it set up.

Anyway, at least I know of a way to get the data.

Thanks again,
stevemcb263

---

### Post by stevemcb263 on 2008-08-25
Cheesehead,

Thanks for the input.

I have learned that it is possible to parse the mbox files that Thunderbird creates for folders, so, in theory, I can parse the contents of the folder that contains my stock data (that's all that's in the folder, thankfully) and output it as a file.

I'll follow your learning suggestions and work at putting together a process that works for me.

Thanks again!
stevemcb263

---

