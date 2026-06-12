---
title: "Conky SSL Email Python Script"
date: 2008-07-25
forum: General Help
---

### Post by kaivalagi on 2008-07-25
[SIZE="1"][COLOR="Green"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*
```
Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]

**_[SIZE="3"][COLOR="Blue"]Intro[/COLOR][/SIZE]_**

This is a simple script to return the count of emails in an inbox, it supports SSL (secure) and standard connections to IMAP and POP3 services on the standard port numbers.

Currently a mail message count of unread emails is returned for IMAP accounts, for POP3 accounts I still need to figure out how I will provide this, currently the total email count is returned. POP3 is a very old and limited protocol, hence the issues.

There is a README with the install, I suggest you give it atleast a quick once over! It can be found in the installation folder, normally following the path of /usr/share/conky<scriptname>/

**_[SIZE="3"][COLOR="Blue"]Basic Install[/COLOR][/SIZE]_**

**[COLOR="Blue"]Method 1: Using apt[/COLOR]**

1) Add the repository to your OS install:
```
sudo add-apt-repository ppa:conky-companions/ppa
```
[INDENT]* Note if you are running 9.10 or below then refer to the PPA link at the end of this post for help on installing from the ppa, good guidance can be found on the launchpad site[/INDENT]

2) Now that is done simply run the following to update your repo cache and install the script: 

```
sudo apt-get update && sudo apt-get install conkyemail

```

**[COLOR=Blue]Method 2: Using deb file[/COLOR]**

Run the .deb file available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR=Blue]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the tar.gz file to an appropriate folder, and edit the conkyEmail script to point to the correct location where conkyEmail.py is. The tar.gz file is available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE="3"][COLOR="Blue"]Usage Help[/COLOR][/SIZE]_**

You can get the current help options at any time by running (change the path as necessary):

```

conkyEmail -h

```

or

```

conkyEmail --help

```

```
Usage: conkyEmail [options]
Options:
  -h, --help            show this help message and exit
  -m SERVERTYPE, --servertype=SERVERTYPE
                        servertype to check [default: POP] The server type
                        options are POP or IMAP
  -s SERVERNAME, --servername=SERVERNAME
                        server name to access [default: pop.mail.yahoo.co.uk]
                        The server name should be either a domain name or ip
                        address
  -o NUMBER, --port=NUMBER
                        Define an alternative port number to use other than
                        the default for the protocol/ssl
  -f FOLDER, --folder=FOLDER
                        [default: Inbox] IMAP folder to check, not applicable
                        for POP mail checks
  -e, --ssl             Use an SSL based connection.
  -u USERNAME, --username=USERNAME
                        username to login with
  -p PASSWORD, --password=PASSWORD
                        Password to login with, if not set the username is
                        used to fetch a 'conky' password from the keyring
  -t FILE, --template=FILE
                        define a template file to generate output in one call.
                        A displayable item in the file is in the form
                        [--servertype=IMAP --ssl --servername=imap.gmail.com
                        --folder=Inbox --username=joebloggs
                        --password=letmein, --connectiontimeout=10]. Note that
                        the short forms of the options are not currently
                        supported! None of these options are applicable at
                        command line when used in templates.
  -i NUMBER, --mailinfo=NUMBER
                        [default: 0] The number of newest emails to output
                        'from' and 'subject' information for. Not applicable
                        at command line when using templates.
  -w NUMBER, --maxwidth=NUMBER
                        [default: 80] Define the number of characters to
                        output per line
  -l NUMBER, --linelimit=NUMBER
                        [default: 0] If above zero this limits the number of
                        lines output for mail info
  -q CHAR, --quote=CHAR
                        [default: "] The character to use for quotations
                        around the subject line
  -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10] Define the number of seconds before a
                        connection timeout can occur. Not applicable at
                        command line when using templates.
  -v, --verbose         request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.
```

The important thing to note now is that the script is called using this in Conky:

```
{execi 1800 conkyEmail ...options...}
```

Rather than something like this as before:

```
{execi 1800 python /path/to/file/conkyEmail.py ...options...}
```

**_[SIZE=3][COLOR=Blue]Development History[/COLOR][/SIZE]_**

Development history going forwards can be seen here [URL="https://code.launchpad.net/%7Econky-companions/+junk/conkyemail"]https://code.launchpad.net/~conky-companions/+junk/conkyemail
[/URL] All packages available from me can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")

---

### Post by Bruce M. on 2008-07-25
Hi kaivalagi,

I never realized there was a problem with the POP3 stuff as I use:

```
${color1}Hay  ${color4}${execi 60 python /home/my_name/Conky/scripts/mail/conkyEmail.py --servertype=POP --servername=pop3.my_isp.com --username=my_name --password=my_password}  ${color1}E-mail$color
```

and my setup "deletes mail" from the server when I download it.

That works for me.
CHIMO!
Bruce

**EDIT:** Hey, I just realized, I have a gmail account as well and it's set to a POP3 account, I can use this there too. (I only want a number anyway).

---

### Post by kaivalagi on 2008-07-25
> **Bruce M. said:**
> Hi kaivalagi,

I never realized there was a problem with the POP3 stuff as I use:

```
${color1}Hay  ${color4}${execi 60 python /home/my_name/Conky/scripts/mail/conkyEmail.py --servertype=POP --servername=pop3.my_isp.com --username=my_name --password=my_password}  ${color1}E-mail$color
```

and my setup "deletes mail" from the server when I download it.

That works for me.
CHIMO!
Bruce

**EDIT:** Hey, I just realized, I have a gmail account as well and it's set to a POP3 account, I can use this there too. (I only want a number anyway).

POP3 doesn't have an unread mail count feature, for that I'd need to keep track of all the emails to understand what is read and what is not, not easy outside of the main mail client used...POP3 is ancient really, outdated and should be disregarded as a protocol.

I recommend switching your gmail account to IMAP based rather then POP...it is more secure generally, and with SSL as well is the bee's knees :)

You can do this via the google mail settings online, and then it's a simple case of changes your account setting in thunderbird/evolution etc...

Your call though, just a recommendation...

---

### Post by Bruce M. on 2008-07-25
> **kaivalagi said:**
> I recommend switching your gmail account to IMAP based rather then POP...it is more secure generally, and with SSL as well is the bee's knees :)

You can do this via the google mail settings online, and then it's a simple case of changes your account setting in thunderbird/evolution etc...

Your call though, just a recommendation...

Thanks K, I'll definately check that out. Don't have an option with my ISP though, I think they only provide POP3. However I will check that out as well.

Regardless, I never leave mails on my server, they are deleted when I download them.

CHIMO!
Bruce

---

### Post by PurposeOfReason on 2008-08-24
Hey, I've been trying to get this to work with my uni and gmail but it always says there are 0 new. Both using IMAP and google is configured right.

---

### Post by wariskampar on 2008-08-25
Same thing here:( I use ivleph's script and it works great.

---

### Post by kaivalagi on 2008-08-25
> **PurposeOfReason said:**
> Hey, I've been trying to get this to work with my uni and gmail but it always says there are 0 new. Both using IMAP and google is configured right.

I'll take a look at some point soon, it used to work...? And nothing is changed ??

---

### Post by kaivalagi on 2008-08-25
[COLOR="Blue"]**[SIZE="4"]UPDATE[/SIZE]**[/COLOR]

Fixed the issue with IMAP counts not working properly, grab the tarball from this post.

I switched to using the "UNSEEN" IMAP search filter instead of "RECENT", recent no longer works as desired?


[COLOR="Blue"]**[SIZE="3"]OPTIONAL[/SIZE]**[/COLOR]

I have updated the first post, as conkyEmail is now available from my personal package archive at launchpad. If you install it this way you'll get any updates with minimal fuss...

Just bear in mind you'll need to change the conky calls from:

```
${execi 1800 python /path/to/script conkyEmail.py ...options...}
```

to:

```
${execi 1800 conkyEmail ...options...}
```

More extensive details to come shortly...

---

### Post by PurposeOfReason on 2008-08-25
Thank you, it works great now!

---

### Post by kaivalagi on 2008-08-25
> **PurposeOfReason said:**
> Thank you, it works great now!

Did you use the new apt based install?

It's working well for conkyForecast...:)

---

### Post by PurposeOfReason on 2008-08-25
> **kaivalagi said:**
> Did you use the new apt based install?

It's working well for conkyForecast...:)
I would but I'm using arch.

---

### Post by kaivalagi on 2008-08-25
> **PurposeOfReason said:**
> I would but I'm using arch.

Sorry, didn't occur to me :lolflag:

If I forget to update attachments at any point, you can download the latest tarball from my launchpad account page here: [https://launchpad.net/~m-buck/+archive](https://launchpad.net/~m-buck/+archive)

---

### Post by wariskampar on 2008-08-25
Thanks kaivalagi. This time it works like a charm:) May I know whether your scripts can display 4 latest message or not.
I would like to do something like this:
Gmail: x new.
1. From:Subject 
2.
3. 
4. 

Yahoo: x new. 
1. From:Subject 
2.
3. 
4. 

Hope I'm not asking too much:) Thanks again

---

### Post by kaivalagi on 2008-08-25
> **wariskampar said:**
> Thanks kaivalagi. This time it works like a charm:) May I know whether your scripts can display 4 latest message or not.
I would like to do something like this:
Gmail: x new.
1. From:Subject 
2.
3. 
4. 

Yahoo: x new. 
1. From:Subject 
2.
3. 
4. 

Hope I'm not asking too much:) Thanks again

Not currently supported, although the python libraries I used can get hold of that detail. I'll have a look at some point to see how tricky it might be.

I'm assuming you'd want the top 4 (could be any number) ordered by newest first?

The tricky thing is making it happen without going back and forth to the mail server on each script call...Interesting challenge I think :)

---

### Post by Bruce M. on 2008-08-25
> **PurposeOfReason said:**
> I would but I'm using arch.
[COLOR="Red"]
OFF TOPIC...[/COLOR]

Just curious here Purpose of Reason but were you using arch when you were helping me with conky back in Dec of last year?

*[SIZE="1"]And just so people know, PoR is one of my mentors.[/SIZE]*
[COLOR="Blue"]**Back on Topic...**[/COLOR]

Nice idea - From:Subject.

Won't play will with someone who is controlling spacing though.
```

Ubuntu Forums: Reply to thread '[all variants] Conky SSL Email Python Script'
Heather: Old Age
Tom Smith: Hello
```
For me, the number of new mails is just fine.  :)

I'd say **K.I.S.S.** it. But those who have seen my conky *know* the **K.I.S.S.** principle was not applied. :lolflag:

Have a nice day.
Bruce

---

### Post by kaivalagi on 2008-08-25
> **Bruce M. said:**
> 
Nice idea - From:Subject.

Won't play will with someone who is controlling spacing though.
```

Ubuntu Forums: Reply to thread '[all variants] Conky SSL Email Python Script'
Heather: Old Age
Tom Smith: Hello
```
For me, the number of new mails is just fine.  :)

I'd say **K.I.S.S.** it. But those who have seen my conky *know* the **K.I.S.S.** principle was not applied. :lolflag:

Have a nice day.
Bruce

I have the "from" and "subject" output working now for IMAP, but like you've said it will be a problem to keep data aligned nicely (we need html tables in conky!)

The only way I can see this sort of working is if the template option is scrubbed and separate exec calls are needed for each mailbox.

The reason being 2 fold:
[LIST=1]
[*]Currently having the possibility of mailbox counts along the same output line (based on a template) means that any multiple line output for extra info will mess the layout up well and truly
[*]An alternative template for "from" and "subject" layout would be troublesome for multiple messages and for the spacing of "from" and "subject" data, if on the same line, due to lengths differing. [/LIST]

The question is, how many people need to retrieve data for more than one mailbox, if only a few exist (like me) can they make do with multiple calls (I can)

I am planning on providing 2 new options, an --accountname=*Yahoo* option, and a --mailinfo=*3* option for the amount of detailed output. If mailinfo if not set or set to zero, current functionality will remain and only count info is returned. Only when you provide a positive mailinfo number will the script then start piecing together info for output, probably in multi-line format like this:

<accountname> <count>
From: <from>    Subject: <subject>
From: <from>    Subject: <subject>
From: <from>    Subject: <subject>

So...what's the consensus? I can do this and the only side effect for keeping current functionality will be the requirement for multiple exec calls for multiple mailboxes...

[COLOR="Navy"]Edit: current output is this:

GMail: 3 New
From: Sainimere Tala <xxxxxxx@xxxxxxx.com> Subject: RE: Amori's pics
From: Admin <xxxxx@xxxxxxxxx.com> Subject: Request
From: "Mark Buck" <xxxxxxxxxxxxxxxxx@yahoo.com.au> Subject: test

or with --mailinfo not set:

3
[/COLOR]

---

### Post by kaivalagi on 2008-08-25
[SIZE="4"][COLOR="Blue"][B]TESTING
[/B][/COLOR][/SIZE]

I've got the --mailinfo option working for both pop and imap, and have left the template functions in place.

Any --mailinfo option in a template is ignored, so the mailinfo option can only be used in command arguments in exec calls.

I've attached the script here...remember to run the script with --help option to get details...

Let me know what you think, if all is okay then I'll publish it through my personal project archive for apt updates...

The changes shouldn't affect your current use of the script :) Please check....

---

### Post by wariskampar on 2008-08-26
Wow! You're as quick as Superman!:)I have tested your scripts but maybe because I do not know how to  use --help, the result is a bit awkward. Anyway, it turn out more a less as expected. Congratulation! and Thanks:) 

As you can see from my screenshot, the red circle is the result if I use ivleph script and the blue one is from yours. I am just curious why imap.googlemail.com is displayed. Besides, do I have option to display:

"Mark Buck":test 

instead of  

From: "Mark Buck" <xxxxxxxxxxxxxxxxx@yahoo.com.au> Subject: test  

In other word can I get the similar result as if I use ivleph. Sorry for being too demanding but I just want to use only one script to handle my email instead of two as for now. Btw, your scripts is well maintained!:)

```
${color 00bfff}Email${color blue}${hr 0}$color
${color aeaeae}Gmail: ${color red}${texeci 60 perl ~/.scripts/conkyGmail.pl n} new.$alignr${color aeaeae}Yahoo: ${color red}${execi 60 python ~/.scripts/conkyEmail.py --servertype=POP --servername=pop.mail.yahoo.com --username=xxx --password=xxx --ssl} new.
${color #696969}${texeci 60 perl ~/.scripts/conkyGmail.pl s}

${color aeaeae}GMail:  ${color1}${execi 60 python ~/.scripts/conkyEmail.py --servertype=IMAP --servername=imap.googlemail.com --username=xxx --password=xxx --ssl --mailinfo=3 }
```

---

### Post by kaivalagi on 2008-08-26
> **wariskampar said:**
> Wow! You're as quick as Superman!:)I have tested your scripts but maybe because I do not know how to  use --help, the result is a bit awkward. Anyway, it turn out more a less as expected. Congratulation! and Thanks:) 

As you can see from my screenshot, the red circle is the result if I use ivleph script and the blue one is from yours. I am just curious why imap.googlemail.com is displayed. Besides, do I have option to display:

"Mark Buck":test 

instead of  

From: "Mark Buck" <xxxxxxxxxxxxxxxxx@yahoo.com.au> Subject: test  

In other word can I get the similar result as if I use ivleph. Sorry for being too demanding but I just want to use only one script to handle my email instead of two as for now. Btw, your scripts is well maintained!:)

```
${color 00bfff}Email${color blue}${hr 0}$color
${color aeaeae}Gmail: ${color red}${texeci 60 perl ~/.scripts/conkyGmail.pl n} new.$alignr${color aeaeae}Yahoo: ${color red}${execi 60 python ~/.scripts/conkyEmail.py --servertype=POP --servername=pop.mail.yahoo.com --username=xxx --password=xxx --ssl} new.
${color #696969}${texeci 60 perl ~/.scripts/conkyGmail.pl s}

${color aeaeae}GMail:  ${color1}${execi 60 python ~/.scripts/conkyEmail.py --servertype=IMAP --servername=imap.googlemail.com --username=xxx --password=xxx --ssl --mailinfo=3 }
```

Try attached

Do we really need the number output for each email? I would sooner lose it to save space in conky...it's just a something you're used to right?

you can set --mailinfo to be how ever many extra lines of info you want, if set to 5 but you have 3 new mails it will only use the space required for the 3 etc...

If this is how you want it then you can use this script for all your mailboxes....it works for ssl/non-ssl pop and imap

Everyone else, can you let me know you're okay with this change, i.e. it doesn't change what the script does for you...

---

### Post by wariskampar on 2008-08-26
Thanks Kaivalagi:) Exactly as I want (hope not sound too selfish:)). Now I will delete the other script confidently. Thanks again.

---

### Post by wariskampar on 2008-08-26
Hello, 

After testing the script, I found a glitch/bug (don't know what exactly). See attachment at the red circle regarding my Gmail account. I sent test email from Yahoo account with the same subject (Test conkyEmail.py). But as as you can see conky do not display it correctly. As for Yahoo, it is ok:)

For the Yahoo account, is your script read any email in Inbox or just the "New" one?


Edit:

One more thing, if I already read the email in Gmail, conky will display "Gmail: ?" instead of "Gmail=0". Yahoo account is ok (Yahoo=0)

---

### Post by kaivalagi on 2008-08-26
> **wariskampar said:**
> Hello, 

After testing the script, I found a glitch/bug (don't know what exactly). See attachment at the red circle regarding my Gmail account. I sent test email from Yahoo account with the same subject (Test conkyEmail.py). But as as you can see conky do not display it correctly. As for Yahoo, it is ok:)

For the Yahoo account, is your script read any email in Inbox or just the "New" one?


Edit:

One more thing, if I already read the email in Gmail, conky will display "Gmail: ?" instead of "Gmail=0". Yahoo account is ok (Yahoo=0)

Yep, I found those myself just now, I'm on it.

The ? is because the script isn't handling noting coming back for imap anymore (too much cut/paste)- easy fix.

The other issue is because I go looking for the keyword From and Subject, no all email data is the same....I might need to use regex instead of simple find and replace :)

Bear with me...

---

### Post by wariskampar on 2008-08-26
Hi kaivalagi, found another bug. Please refer attachment. For Gmail, only one email got displayed even tho there are 2 new emails.

Edit: 

I just receive another email but same problem occur. Seem like only one email being displayed.

---

### Post by kaivalagi on 2008-08-26
wariskampar,

New version attached, I have tried it with a couple of email providers and it seems okay with all...

Better for you too? *fingers crossed*

P.S.--mailinfo=2 to see 2 email from and subject lines

Cheers

---

### Post by wariskampar on 2008-08-26
It works great (so far)!. I keep opening my Hotmail account to get a reply from you. Hehe. It makes me thing it is better to be able to monitor Hotmail within my Conky as well. Just wonder if this great script support Hotmail as well. Thanks again kaivalagi:)

---

### Post by kaivalagi on 2008-08-26
> **wariskampar said:**
> It works great (so far)!. I keep opening my Hotmail account to get a reply from you. Hehe. It makes me thing it is better to be able to monitor Hotmail within my Conky as well. Just wonder if this great script support Hotmail as well. Thanks again kaivalagi:)

No chance for the foreseeable, Hotmail interfacing is not worth the hassle....maybe I'll take a look if I get bored and have no other scripts to work on :)

I've tested with and without the mailinfo option and am happy, so I'll update the apt based package soon too....
[COLOR="Blue"]
Edit: package uploaded, should be available within the next hour, First post also updated with the files.[/COLOR]

---

### Post by wariskampar on 2008-08-27
Hi kaivalagi, conky do not display correct Yahoo info this morning. I got 2 new mails but that do not reflect in conky. Something must break somewhere along the way.

Gmail: 0
Yahoo:

Edit:

Maybe, this problem is not with your script at all. When I try to access Yahoo online, I get this message 

Sorry, Forbidden.
You don't have permission to access this URL on this server.

Please check the URL for proper spelling and capitalization. If you're having trouble locating a destination on Yahoo!, try visiting the Yahoo! home page or look through a list of Yahoo!'s online services. Also, you may find what you're looking for if you try searching below.

I know I get new mail from Evolution. Will keep you informed then

---

### Post by kaivalagi on 2008-08-27
> **wariskampar said:**
> Hi kaivalagi, conky do not display correct Yahoo info this morning. I got 2 new mails but that do not reflect in conky. Something must break somewhere along the way.

Gmail: 0
Yahoo:

Edit:

Maybe, this problem is not with your script at all. When I try to access Yahoo online, I get this message 

Sorry, Forbidden.
You don't have permission to access this URL on this server.

Please check the URL for proper spelling and capitalization. If you're having trouble locating a destination on Yahoo!, try visiting the Yahoo! home page or look through a list of Yahoo!'s online services. Also, you may find what you're looking for if you try searching below.

I know I get new mail from Evolution. Will keep you informed then

Would be nice if it displayed a ? rather than nothing...I'll take a look at some point

---

### Post by kaivalagi on 2008-08-27
> **wariskampar said:**
> Hi kaivalagi, conky do not display correct Yahoo info this morning. I got 2 new mails but that do not reflect in conky. Something must break somewhere along the way.

Gmail: 0
Yahoo:

Edit:

Maybe, this problem is not with your script at all. When I try to access Yahoo online, I get this message 

Sorry, Forbidden.
You don't have permission to access this URL on this server.

Please check the URL for proper spelling and capitalization. If you're having trouble locating a destination on Yahoo!, try visiting the Yahoo! home page or look through a list of Yahoo!'s online services. Also, you may find what you're looking for if you try searching below.

I know I get new mail from Evolution. Will keep you informed then

Well I found an alternative problem with yahoo, they are breaking the rules with their email data structure and not presenting dates in the correct rfc format...so I've updated the script to cope. The script uses the dates to order the mailinfo list in the correct order

See 1.04 in first post or update from apt when available (currently building)

Cheers

---

### Post by wariskampar on 2008-08-27
Do you mean the script was updated. When I replace conkyEmail.py with the new one, Yahoo problem persist (Yahoo= ). I use Method 3 to install so I have to update it manually. 

You're absolutely right. better to display Yahoo=? or Yahoo=Server Down to indicate such condition.

---

### Post by kaivalagi on 2008-08-27
> **wariskampar said:**
> Do you mean the script was updated. When I replace conkyEmail.py with the new one, Yahoo problem persist (Yahoo= ). I use Method 3 to install so I have to update it manually. 

You're absolutely right. better to display Yahoo=? or Yahoo=Server Down to indicate such condition.

The problem you raised is not happening with me, although if you're using the --ssl option you could have problems, yahoo ssl is up and down like a yoyo at the moment.

Try running the conkyEmail exec on the command line with an addition --verbose option to where the problem might be occurring...

---

### Post by wariskampar on 2008-08-27
This may sound stupid, can I ignore --ssl in my code? Btw, here is my current code:

```
${color aeaeae}GMail:  ${color1}${execi 60 python ~/.scripts/conkyEmail.py --servertype=IMAP --servername=imap.googlemail.com --username=xxx --password=xxx --ssl --mailinfo=4 }
 
${color aeaeae}Yahoo: ${color1}${execi 60 python ~/.scripts/conkyEmail.py --servertype=POP --servername=pop.mail.yahoo.com --username=xxx --password=xxx --ssl --mailinfo=4 }
```

---

### Post by kaivalagi on 2008-08-27
> **wariskampar said:**
> This may sound stupid, can I ignore --ssl in my code? Btw, here is my current code:

```
${color aeaeae}GMail:  ${color1}${execi 60 python ~/.scripts/conkyEmail.py --servertype=IMAP --servername=imap.googlemail.com --username=xxx --password=xxx --ssl --mailinfo=4 }
 
${color aeaeae}Yahoo: ${color1}${execi 60 python ~/.scripts/conkyEmail.py --servertype=POP --servername=pop.mail.yahoo.com --username=xxx --password=xxx --ssl --mailinfo=4 }
```

the --ssl option is just that, an option. It's best to use it if supported, and I have been with yahoo pop for some time. Just recently it started playing up...yahoo does it again!

lose the --ssl on your yahoo account and see if that sorts the issue out
keep the ssl on the imap google stuff, that will work just fine

---

### Post by wariskampar on 2008-08-27
Still no luck. I really think Yahoo is the culprit. I still can not access my account online. Same damn error message:)

---

### Post by kaivalagi on 2008-08-27
> **wariskampar said:**
> Still no luck. I really think Yahoo is the culprit. I still can not access my account online. Same damn error message:)

Run this in a terminal session with your correct username and password, to see whats going on...

```
python ~/.scripts/conkyEmail.py --servertype=POP --servername=pop.mail.yahoo.com --username=xxx --password=xxx --ssl --mailinfo=4 --verbose

```

Off for a bit, I'll catch up later

---

### Post by wariskampar on 2008-08-27
I'm so dump earlier I tried this code but with execi at the front:lolflag: Here is the result

=4 --verbose
*** INITIAL OPTIONS:
    servertype: POP
    servername: pop.mail.yahoo.com
    ssl: True
    username: xxx
    password: xxx
    mailinfo: 4
    verbose: True
*** INFO: Logging on to POP server: pop.mail.yahoo.com
*** INFO: Getting message count from POP server: pop.mail.yahoo.com
*** INFO: Extracting message data from POP server: pop.mail.yahoo.com
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Logging of from POP server: pop.mail.yahoo.com
*** ERROR:getOutputText:Unexpected error:  <type 'exceptions.TypeError'>
Traceback (most recent call last):
  File "/home/aznan/.scripts/conkyEmail.py", line 412, in <module>
    email.outputData()
  File "/home/aznan/.scripts/conkyEmail.py", line 392, in outputData
    print output.encode("utf-8")
AttributeError: 'NoneType' object has no attribute 'encode'

Yahoo is accessible but ERROR at getOutputText. What does it mean?

Edit:

Yahoo has back to normal a few minute ago. So, there is nothing wrong with your script (improvement is always welcome though:))

---

### Post by kaivalagi on 2008-08-27
> **wariskampar said:**
> I'm so dump earlier I tried this code but with execi at the front:lolflag: Here is the result

=4 --verbose
*** INITIAL OPTIONS:
    servertype: POP
    servername: pop.mail.yahoo.com
    ssl: True
    username: xxx
    password: xxx
    mailinfo: 4
    verbose: True
*** INFO: Logging on to POP server: pop.mail.yahoo.com
*** INFO: Getting message count from POP server: pop.mail.yahoo.com
*** INFO: Extracting message data from POP server: pop.mail.yahoo.com
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Logging of from POP server: pop.mail.yahoo.com
*** ERROR:getOutputText:Unexpected error:  <type 'exceptions.TypeError'>
Traceback (most recent call last):
  File "/home/aznan/.scripts/conkyEmail.py", line 412, in <module>
    email.outputData()
  File "/home/aznan/.scripts/conkyEmail.py", line 392, in outputData
    print output.encode("utf-8")
AttributeError: 'NoneType' object has no attribute 'encode'

Yahoo is accessible but ERROR at getOutputText. What does it mean?

Edit:

Yahoo has back to normal a few minute ago. So, there is nothing wrong with your script (improvement is always welcome though:))

I'll see what I can do about the output and error messages for this...maybe a nice message saying "**** ERROR: Failed to communication with the server" would do here...along with a ? for output...one day the script will be perfect, just not today ;)

---

### Post by wariskampar on 2008-08-29
Hi kaivalagi, find another bug today. I set --mailinfo=4 but Conky do not display 4 emails as it suppose to do. Please refer attachment

---

### Post by kaivalagi on 2008-08-29
> **wariskampar said:**
> Hi kaivalagi, find another bug today. I set --mailinfo=4 but Conky do not display 4 emails as it suppose to do. Please refer attachment

Something went wrong :) Because the script uses the raw email data so it can handle all email accounts and not just gmail, it is a little more "at risk" with varying email data.

If it's not too late can you run the same with --verbose as an option in the terminal and post the output please (minus your email account details naturally). 

I might have a look tonight but am rather busy over the next few days so I can't promise anything...

Cheers

---

### Post by wariskampar on 2008-08-29
Here is the test result:

```
aznan@aznan-laptop:~$ python ~/.scripts/conkyEmail.py --servertype=POP --servername=pop.mail.yahoo.com --username=xxx--password=xxx --ssl --mailinfo=4 --verbose
*** INITIAL OPTIONS:
    servertype: POP
    servername: pop.mail.yahoo.com
    ssl: True
    username: xxx
    password: xxx
    mailinfo: 4
    verbose: True
*** INFO: Logging on to POP server: pop.mail.yahoo.com
*** INFO: Getting message count from POP server: pop.mail.yahoo.com
*** INFO: Extracting message data from POP server: pop.mail.yahoo.com
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Logging of from POP server: pop.mail.yahoo.com
6 New
1. Corel: "Corel Special Offer: save $70 on world's No. 1 playback software"
2. DonationCoder.com Newsletter: "DC Newsletter for August 28, 2008 - Codename "Dizzying Discounts"
3. The Code Project: "[CodeProject] Daily News - Google introduces Android apps store"
4. lilyy: "[masdutch] JUst for reading time :      10 Great Goals to set for this Ramadan"
```

Please compare this result with the attachment. Something is wrong right:)

---

### Post by kaivalagi on 2008-08-29
> **wariskampar said:**
> Here is the test result:

```
aznan@aznan-laptop:~$ python ~/.scripts/conkyEmail.py --servertype=POP --servername=pop.mail.yahoo.com --username=xxx--password=xxx --ssl --mailinfo=4 --verbose
*** INITIAL OPTIONS:
    servertype: POP
    servername: pop.mail.yahoo.com
    ssl: True
    username: xxx
    password: xxx
    mailinfo: 4
    verbose: True
*** INFO: Logging on to POP server: pop.mail.yahoo.com
*** INFO: Getting message count from POP server: pop.mail.yahoo.com
*** INFO: Extracting message data from POP server: pop.mail.yahoo.com
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Logging of from POP server: pop.mail.yahoo.com
6 New
1. Corel: "Corel Special Offer: save $70 on world's No. 1 playback software"
2. DonationCoder.com Newsletter: "DC Newsletter for August 28, 2008 - Codename "Dizzying Discounts"
3. The Code Project: "[CodeProject] Daily News - Google introduces Android apps store"
4. lilyy: "[masdutch] JUst for reading time :      10 Great Goals to set for this Ramadan"
```

Please compare this result with the attachment. Something is wrong right:)

Are you sure --mailinfo is not 2 in your conkyrc :)

Do me a favour and create a new conkyrc with just the one account conkyEmail call to see whether you get all 4 lines then...

I just found another interesting issue, some subject lines are encoded for various charsets, I am now trying to handle all possibilities with the mail decode_header function...not straight forward...without this you can get subjects like this:

```
=?iso-8859-1?Q?Fr=E5nvaro=2C_autosvar:_Join_my_network_on_LinkedIn?=
```

Fun...

---

### Post by wariskampar on 2008-08-30
I C&P the code from the conkyrc so I'm sure I set --mailinfo=4. I'll try to run conkyEmail with only one account call. Will post the result then:)

---

### Post by kaivalagi on 2008-08-31
> **wariskampar said:**
> I C&P the code from the conkyrc so I'm sure I set --mailinfo=4. I'll try to run conkyEmail with only one account call. Will post the result then:)

Any news? I am confused about this one!

---

### Post by kaivalagi on 2008-08-31
[COLOR="Blue"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

[LIST]
[*]Added header decoding for sender and subject, to handle multiple character sets used.
[/LIST]

If you receive emails with special characters as used in a lot of languages other than English, this will return decent output for from and subject text.

First post updated :)

---

### Post by wariskampar on 2008-08-31
Since the development of this script is 'damn' fast, I have to use Apt method than updating conkyEmail.py manually(at last):)

Anyway, my previous problem still persist (--mailinfo=4 but display max 3 emails). Perhaps I should try --mailinfo=5 to get 4 lines because when running --verbose, the result was correct. Anyway, don't worry kaivalagi. I'm more than happy right now. Please do not stop undating this script:)

---

### Post by kaivalagi on 2008-08-31
> **wariskampar said:**
> Since the development of this script is 'damn' fast, I have to use Apt method than updating conkyEmail.py manually(at last):)

Anyway, my previous problem still persist (--mailinfo=4 but display max 3 emails). Perhaps I should try --mailinfo=5 to get 4 lines because when running --verbose, the result was correct. Anyway, don't worry kaivalagi. I'm more than happy right now. Please do not stop undating this script:)

No chance of a halt to changes, they never seem to stop being required, even if it's just me requiring them for now :)

I can't figure the mailinfo list issue out, I don't have the problem with either IMAP or POP based output...I'll investigate further...soon

---

### Post by HippyRandall on 2008-09-01
ok I must admit that I have not played around with this script before tonight. On that note, I need some help. When trying to run the script from a CLI I get this: (uname and password stripped out of course )

```
conkyEmail --servertype=POP --servername=pop.gmail.com --username=xxx --password=xxx -v --ssl
*** INITIAL OPTIONS:
    servertype: POP
    servername: pop.gmail.com
    ssl: True
    username: XXXXXXXX
    password: XXXXXXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to POP server: pop.gmail.com
*** ERROR:getPOPEmailData:Unexpected error:  <class 'poplib.error_proto'>
?

```
Anyone know what I am doing wrong? Latest ver installed from the PPA

Thanks,
Hippy

---

### Post by kaivalagi on 2008-09-02
> **HippyRandall said:**
> ok I must admit that I have not played around with this script before tonight. On that note, I need some help. When trying to run the script from a CLI I get this: (uname and password stripped out of course )

```
conkyEmail --servertype=POP --servername=pop.gmail.com --username=xxx --password=xxx -v --ssl
*** INITIAL OPTIONS:
    servertype: POP
    servername: pop.gmail.com
    ssl: True
    username: XXXXXXXX
    password: XXXXXXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to POP server: pop.gmail.com
*** ERROR:getPOPEmailData:Unexpected error:  <class 'poplib.error_proto'>
?

```
Anyone know what I am doing wrong? Latest ver installed from the PPA

Thanks,
Hippy

It should be straight forward

Could your gmail account be setup for IMAP (account settings online)?

I am using IMAP for gmail and POP for yahoo...both working

Can you run it with --verbose, and post back the results, it might highlight what is wrong, but by the looks of it there is a protocol error when trying to use POP with your gmail account.

I'd check your gmail account settings first off

---

### Post by Bruce M. on 2008-09-02
> **HippyRandall said:**
> ok I must admit that I have not played around with this script before tonight. On that note, I need some help. When trying to run the script from a CLI I get this: (uname and password stripped out of course )

Well, first off I think you need your uname and password in there!
OHHHHHHHH!!!!! ... just for here. OK, I get it.

> **HippyRandall said:**
> ```
conkyEmail --servertype=POP --servername=pop.gmail.com --username=xxx --password=xxx -v --ssl
*** INITIAL OPTIONS:
    servertype: POP
    servername: pop.gmail.com
    ssl: True
    username: XXXXXXXX
    password: XXXXXXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to POP server: pop.gmail.com
*** ERROR:getPOPEmailData:Unexpected error:  <class 'poplib.error_proto'>
?

```
Anyone know what I am doing wrong? Latest ver installed from the PPA

Thanks,
Hippy

Can't help Hippy, I don't use gmail.com although I do have an account.
Maybe I should set it up.
Hmmmmmmmmm, *Destroyer* project for the day.

Check out what K said.

CHIMO!
Bruce

---

### Post by HippyRandall on 2008-09-02
> **kaivalagi said:**
> It should be straight forward

Could your gmail account be setup for IMAP (account settings online)?

I am using IMAP for gmail and POP for yahoo...both working

Can you run it with --verbose, and post back the results, it might highlight what is wrong, but by the looks of it there is a protocol error when trying to use POP with your gmail account.

I'd check your gmail account settings first off
 
Just woke up but I managed to get gmail working with IMAP but still can't get POP working with my ISP email. Will investigate further after more caffeine and nicotine.
Oh and that output was with the --verbose option.

Hippy

---

### Post by kaivalagi on 2008-09-02
> **HippyRandall said:**
> Just woke up but I managed to get gmail working with IMAP but still can't get POP working with my ISP email. Will investigate further after more caffeine and nicotine.
Oh and that output was with the --verbose option.

Hippy

Doh, of course the --verbose option was used :)

It might be that SSL isn't supported? try POP without --ssl

To be honest though you are better off with IMAP, it is a superior protocol for emails...

IMAP also works better with the script...if for example you keep files on the server in your mail clients POP server settings, you'll get the count including those, IMAP however knows the difference between seen and unseen items so whatever your mail clients settings it will work fine reporting the correct number of new emails.

---

### Post by HippyRandall on 2008-09-02
ok it is now working with my POP restricted ISP. 
New problem: using the --mailinfo=4 option on my IMAP enabled gmail I get this:

```
*** INFO: Searching for new mail on IMAP server: imap.gmail.com
*** INFO: Extracting message data for IMAP server: imap.gmail.com
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** ERROR:getEmailData:Unexpected error:  <type 'exceptions.ValueError'>
*** INFO: Logging of from IMAP server: imap.gmail.com
2 New
1. Freewebs.com: "September Update -- New Templates, Links and Home Page"

```
Notice the "2 New" but it is only returning the subject of the first one. I don't think I will be using this option in a conky environment but still curious why it's not returning both new messages.

Hippy

---

### Post by Bruce M. on 2008-09-02
> **HippyRandall said:**
> Notice the "2 New" but it is only returning the subject of the first one. I don't think I will be using this option in a conky environment but still curious why it's not returning both new messages.

Hippy

Not enough caffeine and or nicotine maybe?
I'll drink one and smoke one here for ya, to give it an extra jolt.

What do I know, I don't leave mail on the server (never have) and I only collect the # of mails.

Works like a charm. \\:D/

CHIMO!
Bruce

---

### Post by kaivalagi on 2008-09-02
> **HippyRandall said:**
> ok it is now working with my POP restricted ISP. 
New problem: using the --mailinfo=4 option on my IMAP enabled gmail I get this:

```
*** INFO: Searching for new mail on IMAP server: imap.gmail.com
*** INFO: Extracting message data for IMAP server: imap.gmail.com
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** ERROR:getEmailData:Unexpected error:  <type 'exceptions.ValueError'>
*** INFO: Logging of from IMAP server: imap.gmail.com
2 New
1. Freewebs.com: "September Update -- New Templates, Links and Home Page"

```
Notice the "2 New" but it is only returning the subject of the first one. I don't think I will be using this option in a conky environment but still curious why it's not returning both new messages.

Hippy

It's the second from or subject line I think...could you debug it? if so put a breakpoint into the getEmailData function and walk through the function...also if not personal can you forward the email to me?

The script does a bunch of stuff with the header records in an email, decoding them to display accented characters etc...

---

### Post by HippyRandall on 2008-09-02
The second undisplayed email was just a test email that I sent myself from another account on netzero. 
I am not the programmer here so I would need some help on stepping through the code etc. My Eclipse know how has been failing me lately :(

---

### Post by kaivalagi on 2008-09-02
> **HippyRandall said:**
> The second undisplayed email was just a test email that I sent myself from another account on netzero. 
I am not the programmer here so I would need some help on stepping through the code etc. My Eclipse know how has been failing me lately :(

In that case could you sent an equivalent test email to my googlemail account? I can test from here then :)

---

### Post by kaivalagi on 2008-09-02
> **HippyRandall said:**
> The second undisplayed email was just a test email that I sent myself from another account on netzero. 
I am not the programmer here so I would need some help on stepping through the code etc. My Eclipse know how has been failing me lately :(

Can you give the attached py script a try instead, I replaced the regex function to cope with varying timezone time info...

Every mail server treats email message data slightly differently, nothing like standards aye!

---

### Post by HippyRandall on 2008-09-02
*** INFO: Logging on to IMAP server: imap.gmail.com
*** INFO: Searching for new mail on IMAP server: imap.gmail.com
*** INFO: Extracting message data for IMAP server: imap.gmail.com
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Logging of from IMAP server: imap.gmail.com
3 New
1. Rick: "test2 another attempt at the conky script"
2. Rick: "test3 yet another attempt at conky email script"
3. Rick: "test4 yet another attempt at conky email script"

damnit now everyone knows my real name ](*,):frown:
it now works properly. I have not looked at the code or the differences between this one you posted and the already installed version but whatever you did...:KS:popcorn:

Hippy

---

### Post by kaivalagi on 2008-09-02
> **HippyRandall said:**
> *** INFO: Logging on to IMAP server: imap.gmail.com
*** INFO: Searching for new mail on IMAP server: imap.gmail.com
*** INFO: Extracting message data for IMAP server: imap.gmail.com
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Logging of from IMAP server: imap.gmail.com
3 New
1. Rick: "test2 another attempt at the conky script"
2. Rick: "test3 yet another attempt at conky email script"
3. Rick: "test4 yet another attempt at conky email script"

damnit now everyone knows my real name ](*,):frown:
it now works properly. I have not looked at the code or the differences between this one you posted and the already installed version but whatever you did...:KS:popcorn:

Hippy

Thanks Rick!

I'll get the update out tonight at some point...

---

### Post by HippyRandall on 2008-09-02
> **kaivalagi said:**
> Thanks Rick!
:confused: who? no one here by that moniker

---

### Post by kaivalagi on 2008-09-02
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Updated the script to handle mailinfo functionality better, it _should_ now cope with all email message data possible.

The first post has been updated and the apt package is available

Cheers

---

### Post by Bruce M. on 2008-09-02
> **HippyRandall said:**
> 1. Rick: "test2 another attempt at the conky script"
2. Rick: "test3 yet another attempt at conky email script"
3. Rick: "test4 yet another attempt at conky email script"

damnit now everyone knows my real name ](*,):frown:

Hippy

Would that be Rick Hippy or Hippy Rick?

CHIMO!
Bruce M.

---

### Post by wariskampar on 2008-09-03
> **kaivalagi said:**
> **[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Updated the script to handle mailinfo functionality better, it _should_ now cope with all email message data possible.

The first post has been updated and the apt package is available

Cheers


Thanks hippi and kavailagi. Hippi for reporting the bug in a very professional ways until kaivalagi can solve it. I should learn how to do the testing. Now, the similar problem that I've been reporting to kaivalagi is solved! After the update, all 4 emails are displayed correctly (and elegantly!):)

---

### Post by lessfield on 2008-09-03
This could be related to my uni's server...
When i call the script w/ mailinfo, it reports address, subject. 
When i call again, all messages are marked as read. 

```
# conkyEmail --servertype=IMAP --servername=imap.uni.edu -username=xxx --password=xxx -v --mailinfo=2

```

*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.uni.edu
    ssl: False
    username: xxx
    password: xxx
    mailinfo: 2
    verbose: True
*** INFO: Logging on to IMAP server: imap.pitt.edu
*** INFO: Searching for new mail on IMAP server: imap.pitt.edu
*** INFO: Extracting message data for IMAP server: imap.pitt.edu
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
*** INFO: Logging of from IMAP server: imap.pitt.edu
2 New
1. addres1@xxx "RE: subj1"
2. None: "subj2"

then when i reissue the command all my  has been marked as read -->

*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.uni.edu
    ssl: False
    username: xxx
    password: xxx
    mailinfo: 2
    verbose: True
*** INFO: Logging on to IMAP server: imap.pitt.edu
*** INFO: Searching for new mail on IMAP server: imap.pitt.edu
*** INFO: Logging of from IMAP server: imap.pitt.edu
0

I had thunderbird open when i made theses calls

---

### Post by kaivalagi on 2008-09-03
> **lessfield said:**
> This could be related to my uni's server...
When i call the script w/ mailinfo, it reports address, subject. 
When i call again, all messages are marked as read. 
I had thunderbird open when i made theses calls

That is strange! When checking emails with the IMAP protocol it should not mark the messages as read...

Have you tried it in the same way with other email accounts such as gmail etc...I wonder whether you get the same result, if you do then it would indicate it relates to the script/thunderbird/your setup...if not then it will be down to your uni imap server.

Is it possible for you to test this out please?

I too run thunderbird whilst conky checks my emails, and all is fine. I just tested it by running conky/killing it and doing that several times...the email notifications stay there...

Once I have a clear picture of what is going on, if it will help I'll delve into the IMAP library code and try and figure it out...

---

### Post by PurposeOfReason on 2008-09-05
I'm trying the new version with arch and get this output.

```

[reasons // ~] ~/.scripts/conkyEmail --template=/home/shawn/.scripts/conkyEmail.template
Traceback (most recent call last):
  File "/home/shawn/.scripts/conkyEmail.py", line 421, in <module>
    email.outputData()
  File "/home/shawn/.scripts/conkyEmail.py", line 402, in outputData
    print output.encode("utf-8")
AttributeError: 'NoneType' object has no attribute 'encode'
[reasons // ~] 

```

---

### Post by kaivalagi on 2008-09-05
> **PurposeOfReason said:**
> I'm trying the new version with arch and get this output.

```

[reasons // ~] ~/.scripts/conkyEmail --template=/home/shawn/.scripts/conkyEmail.template
Traceback (most recent call last):
  File "/home/shawn/.scripts/conkyEmail.py", line 421, in <module>
    email.outputData()
  File "/home/shawn/.scripts/conkyEmail.py", line 402, in outputData
    print output.encode("utf-8")
AttributeError: 'NoneType' object has no attribute 'encode'
[reasons // ~] 

```

Can you run this and post back the results (minus any sensitive info of course...)

```
~/.scripts/conkyEmail --template=/home/shawn/.scripts/conkyEmail.template --verbose
```

Looks like at the very least the script needs for more validation and error messaging added :)

---

### Post by PurposeOfReason on 2008-09-05
```

template --verbose
*** INITIAL OPTIONS:
    servertype: POP
    servername: pop.mail.yahoo.co.uk
    ssl: False
    username: None
    password: None
    mailinfo: 0
    verbose: True
*** ERROR:getOutputTextFromTemplate:Unexpected error:  <type 'exceptions.NameError'>
Traceback (most recent call last):
  File "/home/shawn/.scripts/conkyEmail.py", line 421, in <module>
    email.outputData()
  File "/home/shawn/.scripts/conkyEmail.py", line 402, in outputData
    print output.encode("utf-8")
AttributeError: 'NoneType' object has no attribute 'encode'

```

I don't think its reading the template.

---

### Post by kaivalagi on 2008-09-05
> **PurposeOfReason said:**
> ```

template --verbose
*** INITIAL OPTIONS:
    servertype: POP
    servername: pop.mail.yahoo.co.uk
    ssl: False
    username: None
    password: None
    mailinfo: 0
    verbose: True
*** ERROR:getOutputTextFromTemplate:Unexpected error:  <type 'exceptions.NameError'>
Traceback (most recent call last):
  File "/home/shawn/.scripts/conkyEmail.py", line 421, in <module>
    email.outputData()
  File "/home/shawn/.scripts/conkyEmail.py", line 402, in outputData
    print output.encode("utf-8")
AttributeError: 'NoneType' object has no attribute 'encode'

```

I don't think its reading the template.

Found the bug, I'll be releasing it soon, I'll update when done :)

---

### Post by kaivalagi on 2008-09-05
[COLOR="Purple"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

Fixed a bug in the template functionality and also did a few other things, changes below:

[LIST]
[*]Updated error and info handling and logging
[*]Fixed bug with template based output
[*]Added --version option to output version of script and exit
[/LIST]

The first post has been updated and the apt package is available

Cheers

---

### Post by lessfield on 2008-09-11
sorry was away will test asap
ps great work on this thread and script!

---

### Post by lessfield on 2008-09-11
After marking some old uni-messages as unread via thunderbird and running conkyEmail w/
--servertype=IMAP --servername=imap.uni.edu --username=xx --password=xx --mailinfo=3

and a stout of:  
ERROR: getEmailData:Unexpected error when converting recieve date to datetime:time data did not match format:  data=0 Sep 2008 19:58:26  fmt=%d %b %Y %H:%M:%S

also a conky diplayed
1 New 
1. my_sender: "my_subjet"

then i closed thunderbird, killed and restarted conky and i got 

ERROR: getEmailData:Unexpected error when converting recieve date to datetime:time data did not match format:  data=0 Sep 2008 19:58:26  fmt=%d %b %Y %H:%M:%S
ERROR: getEmailData:Unexpected error when converting recieve date to datetime:time data did not match format:  data=0 Sep 2008 19:58:26  fmt=%d %b %Y %H:%M:%S

w/ conky displaying 
8 New
1. my_sender1: "my_subjet1"
2. my_sender2: "my_subjet2"
3. my_sender3: "my_subjet3"
after refreshing thunderbird all messages were marked as read

this issue does not happen when i use a gmail account. 
my yahoo account is spews some [AUTH] invalid user/password garbage. I tried to set yahoo in 'classic' and 'new Yahoo mail' mode;  w/ and w/o ssl... to no avail. A yahoo-side pop issue?

---

### Post by kaivalagi on 2008-09-11
> **lessfield said:**
> After marking some old uni-messages as unread via thunderbird and running conkyEmail w/
--servertype=IMAP --servername=imap.uni.edu --username=xx --password=xx --mailinfo=3

and a stout of:  
ERROR: getEmailData:Unexpected error when converting recieve date to datetime:time data did not match format:  data=0 Sep 2008 19:58:26  fmt=%d %b %Y %H:%M:%S

also a conky diplayed
1 New 
1. my_sender: "my_subjet"

then i closed thunderbird, killed and restarted conky and i got 

ERROR: getEmailData:Unexpected error when converting recieve date to datetime:time data did not match format:  data=0 Sep 2008 19:58:26  fmt=%d %b %Y %H:%M:%S
ERROR: getEmailData:Unexpected error when converting recieve date to datetime:time data did not match format:  data=0 Sep 2008 19:58:26  fmt=%d %b %Y %H:%M:%S

w/ conky displaying 
8 New
1. my_sender1: "my_subjet1"
2. my_sender2: "my_subjet2"
3. my_sender3: "my_subjet3"
after refreshing thunderbird all messages were marked as read

this issue does not happen when i use a gmail account. 


The date recieved data in the mail message should conform to the RFS standard, if it doesn't this error could happen...Looking at the datetime "0 Sep 2008 19:58:26" why is it "0" ;) there isn't a day in a month that is "0"! The errors don't display in conky and the messages are still listed right?

Also, I think your uni's IMAP server is not working as it should, it should work just as gmail does and isn't. IMAP messages should remain as unseen unless they are read in your client, once read you would then expect them not to show in conky.

> **lessfield said:**
> my yahoo account is spews some [AUTH] invalid user/password garbage. I tried to set yahoo in 'classic' and 'new Yahoo mail' mode;  w/ and w/o ssl... to no avail. A yahoo-side pop issue?

Yahoo has been an on and off affair for me, it is working fine right now for me using pop without ssl, using pop.mail.yahoo.com as the pop server. Remember the username doesn't include the @blah, it is just the text before the @. I assume you know this already ;)

---

### Post by brodos1 on 2008-09-18
Hi:)
I use the conkyemail script and it is great.
I have my own imap server (secure) and the script shows the number og unread messages. But I can not find out where to set the update interval (When it checks for new messages) I see the option --connectiontimeout, but I want it to check for new mail every 5 minutes.
hope someone can help?

---

### Post by kaivalagi on 2008-09-18
> **brodos1 said:**
> Hi:)
I use the conkyemail script and it is great.
I have my own imap server (secure) and the script shows the number og unread messages. But I can not find out where to set the update interval (When it checks for new messages) I see the option --connectiontimeout, but I want it to check for new mail every 5 minutes.
hope someone can help?

The update interval is not set in the script, it is purely a conky setting

In your conkyrc you'll have something like this:

```
${execi 1000 conkyEmail ...settings...}
```

The 1000 is the number of seconds that define the interval for the exec call, just mess about with that.

Take a look at the conky website based documentation to see more details on this:

[http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

Hope that helps

---

### Post by brodos1 on 2008-09-18
> **kaivalagi said:**
> The update interval is not set in the script, it is purely a conky setting

In your conkyrc you'll have something like this:

```
${execi 1000 conkyEmail ...settings...}
```

The 1000 is the number of seconds that define the interval for the exec call, just mess about with that.

Take a look at the conky website based documentation to see more details on this:

[http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

Hope that helps




Yes that helps a lot!! Thank you!!:)
By the way, if I set the --connectiontimeout=0 .Will it then use IMAP idle? (connected all the time)

---

### Post by kaivalagi on 2008-09-18
> **brodos1 said:**
> Yes that helps a lot!! Thank you!!:)
By the way, if I set the --connectiontimeout=0 .Will it then use IMAP idle? (connected all the time)

Nope, I am guessing if the connection timeout (and therefore the network session timeout under the hood) is set to 0 it won't time out at all. This setting if for the time to wait before quitting a inbox status request, if the email server isn't responding this can shorten the time to wait...

You can't have continuous output, it doesn't work that way. Even your email client won't do that I don't think, it will poll based on an interval or when you select an inbox etc. I think by default thunderbird is set to every 10 minutes (i can't remember)

I wouldn't recommend setting a really low execi interval either, you'll swamp your processor with unnecessary tasks. Once every 5 minutes should be more than ample, so {execi 300 ...}

---

### Post by brodos1 on 2008-09-18
> **kaivalagi said:**
> Nope, I am guessing if the connection timeout (and therefore the network session timeout under the hood) is set to 0 it won't time out at all. This setting if for the time to wait before quitting a inbox status request, if the email server isn't responding this can shorten the time to wait...

You can't have continuous output, it doesn't work that way. Even your email client won't do that I don't think, it will poll based on an interval or when you select an inbox etc. I think by default thunderbird is set to every 10 minutes (i can't remember)

I wouldn't recommend setting a really low execi interval either, you'll swamp your processor with unnecessary tasks. Once every 5 minutes should be more than ample, so {execi 300 ...}

Ok.
Thank you for all your help!!:)

---

### Post by kaivalagi on 2008-09-19
> **brodos1 said:**
> Ok.
Thank you for all your help!!:)

No worries :)

---

### Post by kaivalagi on 2008-09-21
[COLOR="DarkOrchid"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

[LIST]
[*]Updated script to work with whitespace characters in command line arguments
[*]Updated example conkyrc to point to the template file correctly
[/LIST]

The attachments on the first post have been updated, and the new package is available via apt.

---

### Post by HippyRandall on 2008-09-28
I am trying to cut down on the number of exec calls in ALL my conkys but have run into a problem.  Calling a template for the 3 email accounts I want to check results in this output on the command line:
```
Conky: desktop window (10000c8) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (2a00001)
Conky: drawing to double buffer
ERROR: getIMAPEmailData:Unexpected error:timed out
ERROR: getIMAPEmailData:Unexpected error:timed out
ERROR: getIMAPEmailData:Unexpected error:timed out
```The top output in the SS is from the template file. The bottom output is from calling them each in turn with exec calls. 
I can't figure out what I am doing wrong. I opened the example template file and edited it with my details and saved it to my home directory. Any ideas?

TIA,
Hippy

Screenshot attached

---

### Post by Bruce M. on 2008-09-28
> **HippyRandall said:**
> I am trying to cut down on the number of exec calls in ALL my conkys but have run into a problem.  Calling a template for the 3 email accounts I want to check results in this output on the command line:

Just a shot in the dark here Hippy, but are you sure you have this line configured properly pointing to the *conkyEmail.template*?
```
--template=/usr/share/conkyemail/example/conkyEmail.template
```

---

### Post by HippyRandall on 2008-09-28
```
${execi 600 conkyEmail --template=/home/hippy/conkyEmail.template}
```and I am not posting my template for obvious reason :D
but rest assured that it is exactly the same as the example, just with my info inserted
I am calling a rhythmbox template in the same way and it works fine BTW
Hippy

---

### Post by Bruce M. on 2008-09-28
> **HippyRandall said:**
> ```
${execi 600 conkyEmail --template=/home/hippy/conkyEmail.template}
```and I am not posting my template for obvious reason :D
but rest assured that it is exactly the same as the example, just with my info inserted
I am calling a rhythmbox template in the same way and it works fine BTW
Hippy

I understand about not posting the template.
Not ever using a template I have no idea, but I see where it might be a better idea as I don't need the "obvious reasons" laying around in a more accessible conky file.... hmmmmmmmmmm

Let me try and see what I come up with.

CHIMO!
Bruce

---

### Post by Bruce M. on 2008-09-28
No errors:
```
bruloo@bruloo:~$ cia
bruloo@bruloo:~$ Conky: desktop window (1400059) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (2000001)
Conky: drawing to double buffer
Conky: desktop window (1400059) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (2c00001)
Conky: drawing to double buffer
Conky: desktop window (1400059) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (2e00001)
Conky: drawing to double buffer
```
This works for me:
```
TEXT
${execi 60 conkyEmail --template=/home/bruloo/Conky/scripts/conkyEmail.template}

${color1}Hay  ${color9}${execi 60 conkyEmail --servertype=POP --servername=po blah blah
```
My template (with obvious mods):
```
You have {--servertype=POP --servername=pop.somewhere.com.ar --username=why_me_of_course --password=you_are_not_cleared_for_this} Email(s).
```
Don't know what to say Hippy. :cry:

CHIMO!
Bruce

---

### Post by HippyRandall on 2008-09-28
it must have something to do with me using an IMAP server then? I'm at a loss. Have to wait for K I guess
 
template file:
```
Hippy Gmail:        {--servertype=IMAP --servername=imap.gmail.com --username=hippyrandall@gmail.com --password=edited out -e}
HippyRandall.com:   {--servertype=IMAP --servername=imap.gmail.com --username=hippy@hippyrandall.com --password=edited out -e}
Webmaster Mail:     {--servertype=IMAP --servername=imap.gmail.com --username=webmaster@hippyrandall.com --password=edited out -e}
```

---

### Post by kaivalagi on 2008-09-28
> **HippyRandall said:**
> it must have something to do with me using an IMAP server then? I'm at a loss. Have to wait for K I guess

Hi Hippy,

Can you post your template (minus your email addresses and login credentials, I want to see what you're trying to do...

I don't bother with the template option but here is what I have for POP yahoo and IMAP google accounts:

```

${voffset 10}${color3}${font Liberation Sans:style=Bold:size=9}Yahoo: ${color1}${font}${execi 300 conkyEmail --mailinfo=3 --servertype=POP --servername=pop.mail.yahoo.com --username=something --password=something}
${voffset 10}${color3}${font Liberation Sans:style=Bold:size=9}Google: ${color1}${font}${execi 300 conkyEmail --mailinfo=3 --servertype=IMAP --servername=imap.googlemail.com --username=something@googlemail.com --password=something --ssl} 

```

---

### Post by HippyRandall on 2008-09-28
Here it is:
```
Hippy Gmail:        {--servertype=IMAP --servername=imap.gmail.com --username=hippyrandall@gmail.com --password=edited out -e}
HippyRandall.com:   {--servertype=IMAP --servername=imap.gmail.com --username=hippy@hippyrandall.com --password=edited out -e}
Webmaster Mail:     {--servertype=IMAP --servername=imap.gmail.com --username=webmaster@hippyrandall.com --password=edited out -e}
```your examples are not calling a template file though? :|

---

### Post by kaivalagi on 2008-09-28
test conkyrc:

```
${execi 300 conkyEmail --template=/home/mark/Desktop/email.template}
```

test template:
```

Yahoo: {--servertype=POP --servername=pop.mail.yahoo.com --username=something --password=something}
GMail: {--servertype=IMAP --servername=imap.googlemail.com --username=something@googlemail.com --password=something --ssl}
```

Working fine

Do your passwords have spaces? Can you try using imap.googlemail.com instead?

Bizarre...

---

### Post by HippyRandall on 2008-09-28
worked out. it was the -e flag I had in my template lines. it needs to be "--ssl" in a template.

---

### Post by kaivalagi on 2008-09-28
> **HippyRandall said:**
> worked out. it was the -e flag I had in my template lines. it needs to be "--ssl" in a template.

I should have realised, no short form options in templates.....

---

### Post by HippyRandall on 2008-09-28
](*,):???: now why would I read a help file? I am a man afterall. Kick it, smack it, punch it...and if it still doesn't work...blame the coder! :D

---

### Post by Bruce M. on 2008-09-29
> **HippyRandall said:**
> ](*,):???: now why would I read a help file? I am a man afterall. Kick it, smack it, punch it...and if it still doesn't work...blame the coder! :D

I agree, I mean who stops the car to ask for directions?

The female of the species.  :)

We KNOW where we're going... that-a-way --->>

---

### Post by HippyRandall on 2008-09-29
--->> that way??? are you sure?
<<--- I thought it was that way?

:D

---

### Post by Bruce M. on 2008-09-29
> **HippyRandall said:**
> --->> that way??? are you sure?
<<--- I thought it was that way?

:D

[CENTER]Ahhhhhhhh, but if we go far enough we meet:
***Me* --->>** *here* **<<--- *you***[/CENTER]

OK, back on topic.

-e or --ssl script or template {sigh} such a silly boo-boo!

They should make CPU's that KNOW what we mean! :lolflag:

I'll have to remember that.

CHIMO!
Bruce

---

### Post by kaivalagi on 2008-10-04
[COLOR="DarkGreen"][SIZE="4"][B]UPDATE
[/B][/SIZE][/COLOR]
I've updated the script, it is available in the first post and via apt, the changes are as follows:

[LIST]
[*]Updated script to use new template methods based on conkyForecast
[*]Updated script to now use "[" and "]" as template brackets rather than "{" and "}" so that the execp/execpi conky command can be used, this enables the use of $font, $color options in the template which conky will then make adjustments for in the output!
[*]Added mailinfo option to template functionality
[*]Updated example files to use execpi conky command
[*]Updated README
[/LIST]

Note the changes to the templates and the requirement for [] rather than {}...

Have fun :)

---

### Post by markp1989 on 2008-10-16
thanks worked perfectly

is there any way to avoid having my password in plain text in my conky rc?

---

### Post by kaivalagi on 2008-10-16
> **markp1989 said:**
> thanks worked perfectly

is there any way to avoid having my password in plain text in my conky rc?

Nope, needs to be plain text I am afraid.

Name your conkyrc with a dot on the front, at least it won't be so obvious to find...

---

### Post by kaivalagi on 2008-10-20
[COLOR="Green"]**[SIZE="5"]UPDATE[/SIZE]**[/COLOR]

Updated the script to handle message dates better, to allow for proper sorting of multiple messages in date order when the mailinfo option is used.

The first has been updated and the apt package is available

Chimo

---

### Post by martynp on 2008-10-25
Hey All,

Seeing as I use conkyForecast and conkyRhythmbox I thought I would switch from just using conkys inbuilt mail counter to conkyEmail.

I have downloaded the .deb (Mark, are you providing an Intrepid PPA yet?)

after installation and setup.........

${execi 60 conkyEmail -e -m IMAP -s imap.aol.com -u xxxx -p xxxx -i 10}

......... it's working fine and drawing down my emails....

However, after the 60 second check it is wiping out the mails shown in my conky (as in marking them read) and therefore wiping them from the conky display. From reading Mark's updates he says it has switched to use UNSEEN.

Any suggestions please. I would like the unread mail to stay in Conky at least until I have read it!

Many Thanks,

Martyn

---

### Post by megadeus on 2008-10-25
I'm having trouble with part of this program, possibly related to special characters in my password.

My university email is all alpha-numeric, and works just fine. My Gmail password, however, contains letters, numbers, and certain ASCII characters that can be found on any keyboard but also have special meanings at the Linux command line. I'm not sure which characters are causing the trouble, and I've tried surrounding the password with quotes and escaping the characters with slashes '\' but neither has worked.

What is the solution to this problem, other than changing my password? :)

---

### Post by kaivalagi on 2008-10-25
> **martynp said:**
> Hey All,

Seeing as I use conkyForecast and conkyRhythmbox I thought I would switch from just using conkys inbuilt mail counter to conkyEmail.

I have downloaded the .deb (Mark, are you providing an Intrepid PPA yet?)

after installation and setup.........

${execi 60 conkyEmail -e -m IMAP -s imap.aol.com -u xxxx -p xxxx -i 10}

......... it's working fine and drawing down my emails....

However, after the 60 second check it is wiping out the mails shown in my conky (as in marking them read) and therefore wiping them from the conky display. From reading Mark's updates he says it has switched to use UNSEEN.

Any suggestions please. I would like the unread mail to stay in Conky at least until I have read it!

Many Thanks,

Martyn

I've done a bit of digging, and I may have come up with something that will resolve the issue for you. Unfortunately this problem of emails being marked as read doesn't happen with gmail which I use, so I cannot test it. All I can say is that what was working still works for me.

I have altered the configuration of the imap message fetch in the script used to display the subject line...

To try out the modification, extract the py file from the attached and try it like this in you conkyrc file:

```
${execi 60 python /path/to/extracted/pyfile/conkyEmail.py -e -m IMAP -s imap.aol.com -u xxxx -p xxxx -i 10}

```

Let me know how you get on, if this fixes things I'll rollout the change in the usual way ;)

Chimo

---

### Post by kaivalagi on 2008-10-25
> **megadeus said:**
> I'm having trouble with part of this program, possibly related to special characters in my password.

My university email is all alpha-numeric, and works just fine. My Gmail password, however, contains letters, numbers, and certain ASCII characters that can be found on any keyboard but also have special meanings at the Linux command line. I'm not sure which characters are causing the trouble, and I've tried surrounding the password with quotes and escaping the characters with slashes '\' but neither has worked.

What is the solution to this problem, other than changing my password? :)

If one of those characters is a $ sign that will probably upset conky quite a bit :(

I can think of a couple of ways to get over this problem, 1) by having the password stored in a separate config file and have it loaded inside the script...2) encrypting the password into a string which has a finite set of characters in use which are acceptable ones...but either way would affect everyone and in most cases be unnecessary. In making this change I would be affecting everybody for a single users problem as far as I am aware...

Can you not just update your password to use characters which do not affect the script, there are only a few that will cause issue. If you go lower and upper case with letters, use numbers and also atleast half of the symbols, you still have an extremely strong password.

---

### Post by martynp on 2008-10-25
That seems to have nailed it Mark!

Thanks for the quick response!

Any chance of adding and Intrepid PPA so I can put you back in my sources and enable me to keep up to date with releases?

Thanks again

---

### Post by kaivalagi on 2008-10-25
> **martynp said:**
> That seems to have nailed it Mark!

Thanks for the quick response!

Any chance of adding and Intrepid PPA so I can put you back in my sources and enable me to keep up to date with releases?

Thanks again

Once I switch to Intrepid I'll upgrade all the packages on launchpad, I plan on switching in the week following the final release...I am in no rush, everything is working just fine :) Mind you, I do want to give the new gnome version a try, and pidgin 2.5 looks good too

The scripts might work okay using the existing hardy based PPA debs in an intrepid sources.list...not sure 'cause I haven't tried.

I'll update the current hardy PPA for conkyEmail at some point tomorrow

Cheers

---

### Post by martynp on 2008-10-25
Goddammit! Why didn't I think of that! Just tried the hardy in intrepid and it worked fine!!!!!! I should now get the update to conkyEmail when you release it. I'll just need to change the exec call back.

Thanks again!

Martyn

---

### Post by kaivalagi on 2008-10-26
[COLOR="Blue"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

I've changed the imap fetch to use '(BODY.PEEK[HEADER])' option rather than '(RFC822)' in an attempt to stop marking items as read with some mail providers.

The first post has been updated, and the apt package is available too

Chimo

---

### Post by jtp755 on 2008-10-31
I have decided to update my conky layout and wanted to add in gmail support but when i try and run the command from the command line i get:
```
/usr/bin/conkyEmail: line 3: /usr/lib/portage/pym: is a directory
```

I am running Gentoo and that might have something to do with it but when i looked at conkyEmail there are only three lines and basically all i see it doing it setting the PYTHONPATH. I downloaded the tar and manually installed it last night.

Here is the /usr/bin/conkyEmail:
```
#! /bin/sh
cd /usr/share/conkyemail/
$PYTHONPATH /usr/bin/python /usr/share/conkyemail/conkyEmail.py "$@"
```

Any ideas?

---

### Post by megadeus on 2008-10-31
Okay, I figured it out. It was my mistake after all and not related to the password. I had mis-typed the mail server in the Template file. :oops:

Anyhow, the script now works beautifully. I'm loving it!

---

### Post by kaivalagi on 2008-10-31
> **jtp755 said:**
> I have decided to update my conky layout and wanted to add in gmail support but when i try and run the command from the command line i get:
```
/usr/bin/conkyEmail: line 3: /usr/lib/portage/pym: is a directory
```

I am running Gentoo and that might have something to do with it but when i looked at conkyEmail there are only three lines and basically all i see it doing it setting the PYTHONPATH. I downloaded the tar and manually installed it last night.

Here is the /usr/bin/conkyEmail:
```
#! /bin/sh
cd /usr/share/conkyemail/
$PYTHONPATH /usr/bin/python /usr/share/conkyemail/conkyEmail.py "$@"
```

Any ideas?

The last line does start the python script with the passed in arguments, otherwise it wouldn't work for everyone.

Are you sure you have the .py file it points to in place too?

Alternatively you can use the .py script directly in conky with something like this:

```
${execi 1800 python /usr/share/conkyemail/conkyEmail.py ...options...}
```

hope that helps

---

### Post by jtp755 on 2008-10-31
Actually i figured out what it was. Apparently on Gentoo...the PYTHONPATH is already being used for portage so i added a 2 on to the end of the conky stuff so its PYTHONPATH2 and everything seems to be working great now!

---

### Post by kaivalagi on 2008-10-31
> **jtp755 said:**
> Actually i figured out what it was. Apparently on Gentoo...the PYTHONPATH is already being used for portage so i added a 2 on to the end of the conky stuff so its PYTHONPATH2 and everything seems to be working great now!

I should be able to loose the "$PYTHONPATH /usr/bin/python" as this should be set already in an OS...

I'll have a play once intrepid is running alright for me :)

---

### Post by kaivalagi on 2008-11-02
[COLOR="Red"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

I've updated the script and added a folder option for imap emails, so a folder can be specified, if not set the default "Inbox" is used.

The first post is updated and the package is available via apt.

Chimo

---

### Post by kaivalagi on 2008-11-02
[COLOR="Green"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

I've published a new package labelled for Intrepid, starting at version 2.0.

The first post has been updated, and the package is available via apt.

To use the new intrepid "labelled" packages via apt, changes to your sources.list are needed. This:

```
deb http://ppa.launchpad.net/m-buck/ubuntu hardy main
deb-src http://ppa.launchpad.net/m-buck/ubuntu hardy main
```

Needs to become this:

```
deb http://ppa.launchpad.net/m-buck/ubuntu intrepid main
deb-src http://ppa.launchpad.net/m-buck/ubuntu intrepid main
```

Currently either hardy or intrepid packages will work with either version of ubuntu.

However going forwards there are no guarantees that packages will continue to work with hardy, development may introduce intrepid specific dependencies. All future revisions will only be available for intrepid.

---

### Post by kaivalagi on 2008-11-10
[SIZE="4"]**[COLOR="Green"]UPDATE[/COLOR]**[/SIZE]

Updated the script as follows:

[LIST]
[*]Updated code to cope with varied message date formats, no one seems to follow the rfcs!
[*]Added --errorlog and --infolog options to log data to a file
[*]Refactored and tidied up
[*]Updated README
[/LIST]

The first post is updated and the apt package will be available shortly

---

### Post by Zachx65 on 2008-11-11
What do I have wrong here, getting error 'Invalid credentials'

```
${voffset -8}${font Martin Vogel's Symbols:size=19}B${font}  Gmail: ${alignr}${font DejaVu Sans:style=Bold:size=8}${execi 1800 conkyEmail --servertype=IMAP --servername=imap.gmail.com --username=??? --password=??? --folder=Inbox --ssl}${font} New email(s)
${endif}${else}
```

(I do have the user name and pass filled in on my end.)

---

### Post by kaivalagi on 2008-11-11
> **Zachx65 said:**
> What do I have wrong here, getting error 'Invalid credentials'

```
${voffset -8}${font Martin Vogel's Symbols:size=19}B${font}  Gmail: ${alignr}${font DejaVu Sans:style=Bold:size=8}${execi 1800 conkyEmail --servertype=IMAP --servername=imap.gmail.com --username=??? --password=??? --folder=Inbox --ssl}${font} New email(s)
${endif}${else}
```

(I do have the user name and pass filled in on my end.)

I think the error says it all. Have you included the full gmail email address as the username, I think google expect it. i.e.

--username=someone@gmail.com or --username=soneone@googlemail.com

---

### Post by HippyRandall on 2008-11-11
> **kaivalagi said:**
> I think the error says it all. Have you included the full gmail email address as the username, I think google expect it. i.e.

--username=someone@gmail.com or --username=soneone@googlemail.com
or perhaps you have not enabled IMAP from the Gmail settings screen?

---

### Post by Zachx65 on 2008-11-11
Thanks for the replies. My problem was I had only entered the credentials once, not the three times the conkyrc I'm using called for... :oops:

---

### Post by Cammy on 2008-11-15
Ok, so after cleaning up and stripping down my conky, I've decided to add a few more items to it.  After looking through the conky variables list, I noticed the "new_mails" variable.  So I code it up and it works great, EXCEPT of course that I have to run my mail client before "new_mails" knows there's mail.

Then I find this thread, and go through the install.  It tells me I have 33 mails, which is puzzling, until I actually READ the documentation and discover that it sees all the emails on a POP account and not just the new ones.

I sure would get a lot more sleep if I would bother to READ the documentation at the beginning and not the end! ](*,)

---

### Post by kaivalagi on 2008-11-15
> **Cammy said:**
> Ok, so after cleaning up and stripping down my conky, I've decided to add a few more items to it.  After looking through the conky variables list, I noticed the "new_mails" variable.  So I code it up and it works great, EXCEPT of course that I have to run my mail client before "new_mails" knows there's mail.

Then I find this thread, and go through the install.  It tells me I have 33 mails, which is puzzling, until I actually READ the documentation and discover that it sees all the emails on a POP account and not just the new ones.

I sure would get a lot more sleep if I would bother to READ the documentation at the beginning and not the end! ](*,)

I feel you! lol

POP is crap....simply put. The only way a script could know what is new is to keep a record of the messages, and do comparisons everytime. ANd even then how does the script know if an email from before should still be "new" or now, cause it's not used to read them...

The easiest option is to setup your mail client to not leave messages on the server, so when it reads them the script finds none on the server.

The best option is to switch to an email provider who has IMAP support, google mail is a good example.

---

### Post by Bruce M. on 2008-11-15
> **kaivalagi said:**
> The easiest option is to setup your mail client to not leave messages on the server, so when it reads them the script finds none on the server.

The best option is to switch to an email provider who has IMAP support, google mail is a good example.

Couldn't agree more.  My POP accounts have been set up to delete mails after I download them for years. And I mean YEARS! I don't like leaving mails on the servers. I have them all here. Every now and then I clean out the ones that are over a year or so old. Unfortunately my ISP doesn't offer IMAP support. Therefore my "count" always reads "actual mails" as new mails, because the minute I open Thunderbird and download them they are deleted from the server.

I have yet to setup conkyEmail to check my gmail account. I really should do that some day. Call me lazy, but I seldom get mail there unless it's spam.

Have a nice day.
Bruce

---

### Post by Cammy on 2008-11-15
I'd have to go the route of switching email providers rather than deleting the mail.  Since I travel a lot, I'm constantly in the position of having to have access to emails I've read from home (itineraries, confirmation numbers, etc) so I leave my mail on the server for 7 days before it auto-deletes.  This has saved me countless times, so I wouldn't be comfortable changing it.

Since my webmail client can tell whether or not something's been read, I suppose it must keep a hash table or something and compare the header or some other item to what's in the table so it knows whether to bold it (unread) or not.  Either way, it probably does not lend itself well to our application.

Thanks for the great script btw.  It is actually really nice, and it's a shame I can't take full advantage of it.

---

### Post by kaivalagi on 2008-11-15
> **Cammy said:**
> I'd have to go the route of switching email providers rather than deleting the mail.  Since I travel a lot, I'm constantly in the position of having to have access to emails I've read from home (itineraries, confirmation numbers, etc) so I leave my mail on the server for 7 days before it auto-deletes.  This has saved me countless times, so I wouldn't be comfortable changing it.

Since my webmail client can tell whether or not something's been read, I suppose it must keep a hash table or something and compare the header or some other item to what's in the table so it knows whether to bold it (unread) or not.  Either way, it probably does not lend itself well to our application.

Thanks for the great script btw.  It is actually really nice, and it's a shame I can't take full advantage of it.

IMAP is definitely the answer for you...it is server orientated mail protocol so if you're on the move a lot it suits...

---

### Post by Bruce M. on 2008-11-15
> **Cammy said:**
> I'd have to go the route of switching email providers rather than deleting the mail.  Since I travel a lot, I'm constantly in the position of having to have access to emails I've read from home (itineraries, confirmation numbers, etc) so I leave my mail on the server for 7 days before it auto-deletes.  This has saved me countless times, so I wouldn't be comfortable changing it.

Since my webmail client can tell whether or not something's been read, I suppose it must keep a hash table or something and compare the header or some other item to what's in the table so it knows whether to bold it (unread) or not.  Either way, it probably does not lend itself well to our application.

Thanks for the great script btw.  It is actually really nice, and it's a shame I can't take full advantage of it.

Hmmmmmm, can your regular email provider be configured to "forward all mail" to another mail box? If so you could get an IMAP server (gmail) have your mail forwarded there and have the best of both worlds.  :D

---

### Post by Cammy on 2008-11-15
> **Bruce M. said:**
> Hmmmmmm, can your regular email provider be configured to "forward all mail" to another mail box? If so you could get an IMAP server (gmail) have your mail forwarded there and have the best of both worlds.  :D

My problem with that is then when I send outgoing mail, it doesn't have my proper "from" address.

---

### Post by Bruce M. on 2008-11-15
> **Cammy said:**
> My problem with that is then when I send outgoing mail, it doesn't have my proper "from" address.

Oops! Yea, never thought of that.  :(

---

### Post by Cammy on 2008-11-15
> **Bruce M. said:**
> Oops! Yea, never thought of that.  :(

lol.  It's even worse with my family, because then they'll add the "new" address to their address book automatically, then do "reply all" and I'll get two copies of everything.

Yes, it's happened before :lolflag:

---

### Post by kaivalagi on 2008-11-15
> **Cammy said:**
> My problem with that is then when I send outgoing mail, it doesn't have my proper "from" address.

set an alternative reply-to address for the new account

---

### Post by super.rad on 2008-11-30
Another one not working correctly for me (it must be something i'm missing or doing wrong)
All conky is displaying is this:
[IMG]http://i274.photobucket.com/albums/jj243/super_rad/screen1.png[/IMG]
but i'd like it to display underneath the unread message count the sender and title in this format
Sender - Title
how would i go about doing this?
my .conkyrc is
```
${execi 600 python /home/fedora/Scripts/conkyEmail.py --servertype=IMAP --servername=imap.googlemail.com --username=*****@googlemail.com --password=***** --ssl} 
```
and my conkyEmail is
```
#! /bin/sh
cd /home/fedora/Scripts/
$PYTHONPATH /usr/bin/python /home/fedora/Scripts/conkyEmail.py "$@"
${voffset 10}${font Terminus:style=Bold:size=9}${color3}Google: ${font}${color1}[--servertype=IMAP --servername=imap.googlemail.com --ssl --username=*****@googlemail.com --password=***** --mailinfo=3]
```
Thanks

---

### Post by kaivalagi on 2008-11-30
> **super.rad said:**
> Another one not working correctly for me (it must be something i'm missing or doing wrong)
All conky is displaying is this:
but i'd like it to display underneath the unread message count the sender and title in this format
Sender - Title
how would i go about doing this?
my .conkyrc is
```
${execi 600 python /home/fedora/Scripts/conkyEmail.py --servertype=IMAP --servername=imap.googlemail.com --username=*****@googlemail.com --password=***** --ssl} 
```
and my conkyEmail is
```
#! /bin/sh
cd /home/fedora/Scripts/
$PYTHONPATH /usr/bin/python /home/fedora/Scripts/conkyEmail.py "$@"
${voffset 10}${font Terminus:style=Bold:size=9}${color3}Google: ${font}${color1}[--servertype=IMAP --servername=imap.googlemail.com --ssl --username=*****@googlemail.com --password=***** --mailinfo=3]
```
Thanks

Just lose the second shell script altogether, I am not sure what you are trying to do there :confused: No conky stuff should exist there...
Then added the --mailinfo=3 option to the .conkyrc execi for emails...

---

### Post by super.rad on 2008-11-30
Yup working, not sure what I was doing, reading/editing too many files at once and wrote things in the wrong files.
Thanks again

---

### Post by Steve Fisher on 2008-12-03
I'm having trouble with my Yahoo account, but I can't see what's wrong with this -
```
TEXT
${color0}MAIL:${color}
${color1}Yahoo: ${execi 300 conkyEmail --mailinfo=3 --servertype=POP --servername=pop.mail.yahoo.co.uk --username=*****@yahoo.co.uk --password=*****}
Google: ${execi 300 conkyEmail --mailinfo=3 --servertype=IMAP --servername=imap.googlemail.com --username=*****@googlemail.com --password=***** --ssl}${color}
```
It's a pretty basic config, just for testing. The Yahoo entry just shows as a "?". Googlemail is working fine.

The only thing I can possibly think of is that my username contains a "_" (underscore). Could this be throwing Conky off?

---

### Post by Steve Fisher on 2008-12-03
Argghh!!

Found the answer.

[http://help.yahoo.com/l/uk/yahoo/mail/original/manage/pop-31.html](http://help.yahoo.com/l/uk/yahoo/mail/original/manage/pop-31.html)

> The ability to access Yahoo! Mail via a POP3 email client is only available to customers of Mail Plus. If you have not purchased the Mail Plus service, you will be unable to retrieve messages via an email client (such as Outlook or Outlook Express). You can determine whether or not you've purchased this service by visiting Yahoo’s password-protected secure billing site.

Nvm, I've set it up to forward all my mail to my Googlemail account now anyway.

---

### Post by kaivalagi on 2008-12-03
> **Steve Fisher said:**
> Argghh!!

Found the answer.

[http://help.yahoo.com/l/uk/yahoo/mail/original/manage/pop-31.html](http://help.yahoo.com/l/uk/yahoo/mail/original/manage/pop-31.html)



Nvm, I've set it up to forward all my mail to my Googlemail account now anyway.

Just so you now, yahoo mail accounts are normally accessed using a username without the domain after it...i.e. I access using username=kaivalagi_ni_viti

---

### Post by v3xtra on 2008-12-10
Hi there!  I am using your script and I love it!  It is simple and easy to use.  You are a fantastic programmer, and are doing a lot for the conky community.

As I have been using it though, I have come into an issue that I cannot figure out.  I have a university e-mail account and I have e-mail rules for my inbox that go to seperate folders.  95% of the time there is nothing in my Inbox, but in seperate folders.  I have tried to use the folder option in IMAP but it only comes up with a question mark.  Here is the portion of .conkyrc that I believe is necessary:

```
( ${execi 300 conkyEmail -m IMAP -s minermail.mst.edu -e -folder=SigEp -u ******* -p ******* } )
```

The basic command without the folder option shows the correct umber of e-mails in the inbox, but I cannot figure out how to get it to read the number of e-mails in the folders!  Any insight would be fantastic, as I have some folders that I need to watch regularly!

Thanks again!

EDIT:  Wow, looking back at it, I found my error.  The command is --folder=, not -folder=.  Sorry for the waste of time!

---

### Post by kaivalagi on 2008-12-11
> **v3xtra said:**
> EDIT:  Wow, looking back at it, I found my error.  The command is --folder=, not -folder=.  Sorry for the waste of time!

No worries, it's always the simple things in the end :)

Glad it's doing what it needs to, any questions just shout!

---

### Post by supersobbie on 2008-12-12
ok first let me say thanks for all the hard work on this!! it looks great.

OK my question is how to I limit the amount of characters that are outputted for the subject.  I have a narrow conky on the right side of my screen.... I check my gamil and everything works great.  it returns the count and the first 3 unread as I would expect.  the only things is when it prints out the first 3 all the sudden my conky stretches to over half the screen to fit the subject line in the email.  is there any way to have it trunkate after a certain amount of characters?

Maybe I am just missing something.

Thanks a ton.

SoBBie

PS I am not using the template and here is the line that I have in conkyrc:
${voffset 4}${font StyleBats:size=14}C${font}   GMail Total: ${execi 600 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --username=me@gmail.com --password=pass1 --ssl}

---

### Post by kaivalagi on 2008-12-12
> **supersobbie said:**
> ok first let me say thanks for all the hard work on this!! it looks great.

OK my question is how to I limit the amount of characters that are outputted for the subject.  I have a narrow conky on the right side of my screen.... I check my gamil and everything works great.  it returns the count and the first 3 unread as I would expect.  the only things is when it prints out the first 3 all the sudden my conky stretches to over half the screen to fit the subject line in the email.  is there any way to have it trunkate after a certain amount of characters?

Maybe I am just missing something.

Thanks a ton.

SoBBie

PS I am not using the template and here is the line that I have in conkyrc:
${voffset 4}${font StyleBats:size=14}C${font}   GMail Total: ${execi 600 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --username=me@gmail.com --password=pass1 --ssl}

The script has no function to restrict the output width, but in theory there are other ways in conky.

In your conkyrc file you need to define the maximum width before the TEXT line, the window will never go beyond this size then:

```
maximum_width 300
```

300, is 300 pixels...

That should sort it for you

---

### Post by gcranston on 2008-12-13
Is there any way to get this script to display the subjects of new emails like gmail_parser.py?  Does anyone know of anything like that?

---

### Post by kaivalagi on 2008-12-13
> **gcranston said:**
> Is there any way to get this script to display the subjects of new emails like gmail_parser.py?  Does anyone know of anything like that?

--mailinfo option

The first post has a screenshot with 2 subjects displayed. The example files also demonstrate the settings. Read the README in the first post for more info.....

---

### Post by biohazardousguy on 2008-12-15
Hi, 
A stupid question maybe, but this script can pick up new mail from evolution in-box? If yes, how should I do it?
Thanks

---

### Post by kaivalagi on 2008-12-15
> **biohazardousguy said:**
> Hi, 
A stupid question maybe, but this script can pick up new mail from evolution in-box? If yes, how should I do it?
Thanks

I am assuming that the evolution inbox is populated via connecting to a pop or imap server first, this script will do the same without marking the emails as read

Hope that helps

---

### Post by altonbr on 2008-12-15
This is an amazing application, thank you!

_This is my story:_

I installed the Intrepid apt source.
I installed conkyEmail.
I ran conkyEmail with my settings and it worked:
```
conkyEmail -m IMAP -s imap.server.com --ssl -u username -p password -i 10 --errorlogfile=/home/brett/Desktop/errorlog --infologfile=/home/brett/Desktop/infolog
```
and received:
> 7 New
1. Name: "Re: ..."
2. Name: "Re: ..."
3. Name: "Re: ..."
4. Name: "Re: ..."
5. Name: "Re: ..."
6. Name: "Re: ..."
7. Name: "Re: ..."

The infolog even said:
> 2008-12-15 15:15:49 INFO: Logging on to IMAP server: imap.server.com
2008-12-15 15:15:49 INFO: Searching for new mail on IMAP server "imap.server.com" in folder "Inbox"
2008-12-15 15:15:49 INFO: Extracting message data for IMAP server: imap.server.com
2008-12-15 15:15:49 INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
2008-12-15 15:15:50 INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
2008-12-15 15:15:50 INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
2008-12-15 15:15:50 INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
2008-12-15 15:15:50 INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
2008-12-15 15:15:50 INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
2008-12-15 15:15:50 INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
2008-12-15 15:15:50 INFO: Logging of from IMAP server: imap.server.com

Conky works with this line:
```
${execi 180 conkyEmail -m IMAP -s imap.server.com --ssl -u username -p password -i 10 --errorlogfile=/home/brett/Desktop/errorlog --infologfile=/home/brett/Desktop/infolog}
```

Thank you, thank you, thank you!

Have to talked to MOTU to get this included for Jaunty?

---

### Post by kaivalagi on 2008-12-15
> **altonbr said:**
> 

Thank you, thank you, thank you!

Have to talked to MOTU to get this included for Jaunty?

My pleasure :)

I wont bother going through all the hassle of getting it into Jaunty, it is fairly straight forward to use via my PPA. I might do so with my new app though (see my sig)...we'll see how it goes.

---

### Post by sknud on 2008-12-23
Thanks for an awesome plugin, it works well for my unsecured imap server.
However one of my providers have imaps on port 993, which i cant seem to connect to. Is it possible to have the option to specify which port the plugin will connect to?

---

### Post by kaivalagi on 2008-12-23
Fair enough request, I don't see a problem in adding a port option to the script, which overrides the default port for communication.

I am not sure when I'll get it done though...it is Christmas after all and I have a new toy to play with (R/C Nitro 4x4 - oh...the kid in me).

If you dont mind hacking the script yourself (useful test too) then follow these simple steps.

1) Open the script for editing through sudo (change the location if not installed via apt):

```
gksudo gedit /usr/share/conkyemail/conkyEmail.py
```

2) Find the following in the script (should be line 366):

```
imap = imaplib.IMAP4_SSL(servername)
```

3) Change the above line to this and save:

```
imap = imaplib.IMAP4_SSL(servername[COLOR="Red"], 993[/COLOR])
```

That _should_ do the trick, the imaplib object supports port numbers with an optional parameter like this.

The longer term solution will be a port option which alters the call as necessary...

Hope that helps

---

### Post by Bruce M. on 2008-12-23
**OFFTOPIC**

> **kaivalagi said:**
> I have a new toy to play with (R/C Nitro 4x4 - oh...the kid in me).

Picture please, using your second newest toy.   :)

Chimo!
Bruce

---

### Post by kaivalagi on 2008-12-24
> **Bruce M. said:**
> **OFFTOPIC**

Picture please, using your second newest toy.   :)

Chimo!
Bruce

'Cause I'm lazy and my camera is all packed away right now, I'll just link to an image from a google search, exact same model and colour as mine though...more pictures to come which I'll possibilly setup on my site in the near future...

[IMG]http://farm4.static.flickr.com/3108/2855750895_00d9ab59e9.jpg?v=0[/IMG]

The manufacturer site for it is [here.]("http://www.hpieurope.com/kit-info.php?partNo=10411&lang=en")

I've only just run it in, done it all by the book. Not thrashed it yet at all....I have higher rated fuel in it today and will be tuning the carb settings to get a nice mix.

Next thing on the shopping list is a fail over so if it goes out of range, batteries die or interference hits, the throttle drops back to idle! Well worth the out lay I think :)

Couple of you tubes videos to give you an idea ;)
[http://uk.youtube.com/watch?v=8plAfrrAdO8](http://uk.youtube.com/watch?v=8plAfrrAdO8)
[http://uk.youtube.com/watch?v=IEMA4-XdawQ](http://uk.youtube.com/watch?v=IEMA4-XdawQ)

I wonder how long it will be before I break something!

---

### Post by Bruce M. on 2008-12-24
> **kaivalagi said:**
> I wonder how long it will be before I break something!

WoW!!!!!!!!!  At 73+ km/hr it just may be faster than you think.

What a neat toy!  :D

Have fun!!!!!

CHIMO!
Bruce

---

### Post by kaivalagi on 2008-12-24
> **Bruce M. said:**
> WoW!!!!!!!!!  At 73+ km/hr it just may be faster than you think.

What a neat toy!  :D

Have fun!!!!!

CHIMO!
Bruce

I'm already looking at the "hop up" options....aluminium replacement wishbones, shock towers etc etc...I almost want to break something so I have the excuse to buy shiny new and better parts :)

Maybe I should start a new thread in the community cafe :)

---

### Post by Bruce M. on 2008-12-24
> **kaivalagi said:**
> I'm already looking at the "hop up" options....aluminium replacement wishbones, shock towers etc etc...I almost want to break something so I have the excuse to buy shiny new and better parts :)

Maybe I should start a new thread in the community cafe :)

Hahahaha, that's the kid in all of us talking.

Hey, good idea: **Boy Toys:**
Then the for the first line:
**Sub-Topic: The R/C Nitro 4x4**
Leaves it open for other's to talk about their "toys"  :D

---

### Post by HarshReality on 2008-12-27
Too bad it cant parse or something for the free email accounts that don not allow for pop (yahoo has to pay like 20 a year now)

---

### Post by kaivalagi on 2008-12-27
> **HarshReality said:**
> Too bad it cant parse or something for the free email accounts that don not allow for pop (yahoo has to pay like 20 a year now)

Gmail is a good option...at least it was when I last checked...

---

### Post by altonbr on 2008-12-27
> **HarshReality said:**
> Too bad it cant parse or something for the free email accounts that don not allow for pop (yahoo has to pay like 20 a year now)

Use gmail, works for me.

---

### Post by sknud on 2008-12-28
> **kaivalagi said:**
> Fair enough request, I don't see a problem in adding a port option to the script, which overrides the default port for communication.

I am not sure when I'll get it done though...it is Christmas after all and I have a new toy to play with (R/C Nitro 4x4 - oh...the kid in me).

If you dont mind hacking the script yourself (useful test too) then follow these simple steps.

1) Open the script for editing through sudo (change the location if not installed via apt):

```
gksudo gedit /usr/share/conkyemail/conkyEmail.py
```

2) Find the following in the script (should be line 366):

```
imap = imaplib.IMAP4_SSL(servername)
```

3) Change the above line to this and save:

```
imap = imaplib.IMAP4_SSL(servername[COLOR="Red"], 993[/COLOR])
```

That _should_ do the trick, the imaplib object supports port numbers with an optional parameter like this.

The longer term solution will be a port option which alters the call as necessary...

Hope that helps

Thanks for looking into this. This quick fix worked for me.
Too bad i really suck at scripting, or i'd fix this permanently for you :)

---

### Post by lucesei on 2009-01-01
Hi, I'm using your script with Gmail. Everything is fine, but I need a small mod. When I set a value for mailinfo, I get the oldest unread messages, while I need he newest ones. For example: if there are 10 unread messages and I set mailinfo to 4, I get sender+subject of mails 1-2-3-4, while I need sender+subject of mails 10-9-8-7, newest on top, oldest at the bottom, like the order in the mailbox. Is this possible? Looking forward to a reply and thank you in advance for your help.

Luca

---

### Post by kaivalagi on 2009-01-02
> **lucesei said:**
> Hi, I'm using your script with Gmail. Everything is fine, but I need a small mod. When I set a value for mailinfo, I get the oldest unread messages, while I need he newest ones. For example: if there are 10 unread messages and I set mailinfo to 4, I get sender+subject of mails 1-2-3-4, while I need sender+subject of mails 10-9-8-7, newest on top, oldest at the bottom, like the order in the mailbox. Is this possible? Looking forward to a reply and thank you in advance for your help.

Luca

mmmmm, that is the intended behaviour.

Emails are sorted by received date...but obviously the wrong way around

I'm making the change now...to the sort method

Update shortly :)

---

### Post by kaivalagi on 2009-01-02
[COLOR="DarkOrange"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

The script has been updated as follows:

[LIST]
[*]Fixed email list sorting to be reversed, now newest email is first in list
[*]Updated mailinfo and connectiontimeout options to use correct datatype to stop strange behaviour
[/LIST]

The first post has been updated and the apt package is available too

Cheers

---

### Post by lucesei on 2009-01-02
> **kaivalagi said:**
> mmmmm, that is the intended behaviour.

Emails are sorted by received date...but obviously the wrong way around

I'm making the change now...to the sort method

Update shortly :)

Just installed the update, now everything works perfectly, just like I needed. Thank you so much for the quick reaction, and my compliments for your work with conky.

Luca

---

### Post by kaivalagi on 2009-01-03
> **lucesei said:**
> Just installed the update, now everything works perfectly, just like I needed. Thank you so much for the quick reaction, and my compliments for your work with conky.

Luca

Nice to hear, thanks :)

---

### Post by Tick-Tock on 2009-01-06
> **kaivalagi said:**
> No chance for the foreseeable, Hotmail interfacing is not worth the hassle....maybe I'll take a look if I get bored and have no other scripts to work on :)

I've tested with and without the mailinfo option and am happy, so I'll update the apt based package soon too....
[COLOR="Blue"]
Edit: package uploaded, should be available within the next hour, First post also updated with the files.[/COLOR]

Hi. I use your script with gmail and it works well, thank you for your job.
But I can't understand if hotmail is supported and if yes, what variables I've to put in the command line: hotmail hasn't pop3 or imap, for what I know...

---

### Post by kaivalagi on 2009-01-06
> **Tick-Tock said:**
> Hi. I use your script with gmail and it works well, thank you for your job.
But I can't understand if hotmail is supported and if yes, what variables I've to put in the command line: hotmail hasn't pop3 or imap, for what I know...

No sorry hotmail is not supported, as it does not present email info over either the pop or imap protocols...instead it uses it's own proprietary protocol over http which doesn't work in all linux email clients as far as I am aware.

There are tricks to get hotmail working with a mail client, if you search these forums for those and get them working, then the script can be used in just the same way as the mail client would be setup. Hotway is one option, take a look here: [http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

---

### Post by lucesei on 2009-01-13
Hi, thi is the error I get when I use the template output and mailinfo>0 with gmail:
> ERROR: getOutputData:Unexpected error:can't compare datetime.datetime to NoneType
This is my template:
> [--servertype=IMAP --servername=imap.gmail.com --ssl --username=myusername --password=mypassword --mailinfo=10]
When mailinfo is set to zero (retrieves only an unread mails count), everything works fine.
I experimented a little with trhe messages on my gmail account, and I am sure the problem is in how gmail displays the 2009 dates. If I set as unread only the 2008 messages (that are listed with a month/day/year format), your script works correctly, displaying both a total unread count and the mail subjects.
When I set as unread the 2009 messages, that have a month (three letter)/day format, your script returns the error.
Same error if I mix 2008 and 2009 messages.
I hope I have been helpful to you, and I thank you in advance for a fix of the problem.

Luca

---

### Post by kaivalagi on 2009-01-14
> **lucesei said:**
> Hi, thi is the error I get when I use the template output and mailinfo>0 with gmail:

This is my template:

When mailinfo is set to zero (retrieves only an unread mails count), everything works fine.
I experimented a little with trhe messages on my gmail account, and I am sure the problem is in how gmail displays the 2009 dates. If I set as unread only the 2008 messages (that are listed with a month/day/year format), your script works correctly, displaying both a total unread count and the mail subjects.
When I set as unread the 2009 messages, that have a month (three letter)/day format, your script returns the error.
Same error if I mix 2008 and 2009 messages.
I hope I have been helpful to you, and I thank you in advance for a fix of the problem.

Luca

There is **one** standard for the email received date format inside the message headers, you would think that this means all emails would have this same format date then....no....none of the mail providers seem to pay close attention to it. ](*,)

The error looks like it is caused when trying to sort the email data when one or more emails has no received date set. I have set a default value for message date if nothing can be obtained from the email headers, that way there should always be a date value and the sort should work regardless of the email date format....

I've attached a new version of script package, can you install it and try it out

If this doesn't work I'll need to try and reproduce the error locally and step through the code...

*fingers crossed*

---

### Post by lucesei on 2009-01-14
> **kaivalagi said:**
> There is **one** standard for the email received date format inside the message headers, you would think that this means all emails would have this same format date then....no....none of the mail providers seem to pay close attention to it. ](*,)

The error looks like it is caused when trying to sort the email data when one or more emails has no received date set. I have set a default value for message date if nothing can be obtained from the email headers, that way there should always be a date value and the sort should work regardless of the email date format....

I've attached a new version of script package, can you install it and try it out

If this doesn't work I'll need to try and reproduce the error locally and step through the code...

*fingers crossed*

Good News! conkyEmail v. 2.03 solves the problem I pointed out yesterday. I did a test with a mix of mails just received, mails 2 or 3 days old, 1 week old, and an assortment of months from 2008. All of them are displayed correctly and in the correct order. Good work!.
Now that I look at the thing from a different point of view, I must apologise with you: it wasn't a bug in your script, it's a bug in Gmail!!
They use 3 different ways of displaying dates:
- within 24 hours old = reception time (12 hour format, am/pm)
- current month = 3-letter month, day
- rest = year/month/day
No wonder it's so difficult to sort out the dates. But then again Google is so HUGE, that rather than complying to the standards, they make their own ones...
Thanks again for all the effort you put into this work. Regards,

Luca

---

### Post by kaivalagi on 2009-01-15
> **lucesei said:**
> Good News! conkyEmail v. 2.03 solves the problem I pointed out yesterday. I did a test with a mix of mails just received, mails 2 or 3 days old, 1 week old, and an assortment of months from 2008. All of them are displayed correctly and in the correct order. Good work!.
Now that I look at the thing from a different point of view, I must apologise with you: it wasn't a bug in your script, it's a bug in Gmail!!
They use 3 different ways of displaying dates:
- within 24 hours old = reception time (12 hour format, am/pm)
- current month = 3-letter month, day
- rest = year/month/day
No wonder it's so difficult to sort out the dates. But then again Google is so HUGE, that rather than complying to the standards, they make their own ones...
Thanks again for all the effort you put into this work. Regards,

Luca

Thanks for the heads up on the formats, just so I am 100% certain on them, could you post actual data for each date format you've mentioned please?

I would like to setup the date extraction in the script to use all known formats, one after the other when errors occur...

Cheers

---

### Post by kaivalagi on 2009-01-15
[COLOR="Blue"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

The script now uses default values for message date/subject/sender if nothing can be obtained from the email headers. This ensures there should always be a date value and the list sort should work regardless of the email date format...

The first post has been updated and the new apt package will be available soon

---

### Post by lucesei on 2009-01-15
> **kaivalagi said:**
> just so I am 100% certain on them, could you post actual data for each date format you've mentioned please?

Cheers

Sure, I'll be glad.

- Format 1 = within 24 hours:
> - On the inbox page: 2:11 am
- Short form, on the message page: 2:11 AM (21 hours ago)
- In the message header: date	Thu, Jan 15, 2009 at 2:11 AM
- Format 2 = within the current month:
> - On the inbox page: Jan 14
- Short form, on the message page: Jan 14 (2 days ago)
- In the message header: date	Wed, Jan 14, 2009 at 12:12 AM

- Format 3 = the rest:
> - On the inbox page: 12/31/08
- Short form, on the message page: 12/31/08
- In the message header: date	Wed, Dec 31, 2008 at 3:58 PM

I hope this is clear enough. Tell me if you need more details.

Luca

---

### Post by kaivalagi on 2009-01-16
> **lucesei said:**
> 

I hope this is clear enough. Tell me if you need more details.

Luca

That's great, thanks

---

### Post by Fluidity UK on 2009-01-21
Hi, 

I'm having problems checking email from my Zenbe account. Even though I have new emails conkyEmail always returns 0. I have tried it with my Gmail account also and it seems to work fine with that.

Here's my script output:

```

conkyEmail --servertype=IMAP --servername=imap.zenbe.com --ssl --username=**** --password=**** --connectiontimeout=10 --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.zenbe.com
    folder: Inbox
    ssl: True
    username: ****
    password: ****
    mailinfo: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Logging on to IMAP server: imap.zenbe.com
INFO: Searching for new mail on IMAP server "imap.zenbe.com" in folder "Inbox"
INFO: Logging of from IMAP server: imap.zenbe.com
0

```

Any ideas?

Thanks

--

Rich

---

### Post by kaivalagi on 2009-01-21
> **Fluidity UK said:**
> Hi, 

I'm having problems checking email from my Zenbe account. Even though I have new emails conkyEmail always returns 0. I have tried it with my Gmail account also and it seems to work fine with that.

Here's my script output:

```

conkyEmail --servertype=IMAP --servername=imap.zenbe.com --ssl --username=**** --password=**** --connectiontimeout=10 --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.zenbe.com
    folder: Inbox
    ssl: True
    username: ****
    password: ****
    mailinfo: 0
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Logging on to IMAP server: imap.zenbe.com
INFO: Searching for new mail on IMAP server "imap.zenbe.com" in folder "Inbox"
INFO: Logging of from IMAP server: imap.zenbe.com
0

```

Any ideas?

Thanks

--

Rich

The standard folder to check for emails on an IMAP server is "Inbox" which is the default for the script. Maybe Zenbe uses a different folder name? Check you mail client to see where all your emails go to...

If you need an alternative folder use the --folder option in the exec call. Help detail on it are as follows:

```
  -f FOLDER, --folder=FOLDER
                        [default: Inbox] IMAP folder to check, not applicable
                        for POP mail checks
```

I can't think of any other reason, the script seems happy to login, check and logout...

Hope that helps

---

### Post by detroit/zero on 2009-01-26
Hi Kaivalagi,

I've been using your Email Script for a few weeks now. I'm on Hardy Heron and installed from your repo so I can stay current with updates.

I'm pretty sure it's an issue with your script, but not necessarily. When my emails are fetched for display, special characters aren't being shown. I'm currently living in Poland, and for my Polish email address, senders and subjects often contain the special characters &#261;&#263;&#281;ó&#347;&#380;&#378;, but end up displayed as code. I realize that Conky has the *override_utf8_locale* setting, and I have that set to 'yes'.

I've attached a couple screenshots - two from my ConkyEmail display (one showing the code being displayed and one showing that Conky is indeed set to display these chars), one from Thunderbird showing the actual sender and subject with the special chars, and I've attached my conky-email config.

Thanks in advance for any help you can give me!

---

### Post by kaivalagi on 2009-01-26
> **detroit/zero said:**
> Hi Kaivalagi,

I've been using your Email Script for a few weeks now. I'm on Hardy Heron and installed from your repo so I can stay current with updates.

I'm pretty sure it's an issue with your script, but not necessarily. When my emails are fetched for display, special characters aren't being shown. I'm currently living in Poland, and for my Polish email address, senders and subjects often contain the special characters &#261;&#263;&#281;ó&#347;&#380;&#378;, but end up displayed as code. I realize that Conky has the *override_utf8_locale* setting, and I have that set to 'yes'.

I've attached a couple screenshots - two from my ConkyEmail display (one showing the code being displayed and one showing that Conky is indeed set to display these chars), one from Thunderbird showing the actual sender and subject with the special chars, and I've attached my conky-email config.

Thanks in advance for any help you can give me!

First off can you try using the intrepid repo instead? It is updated whereas the hardy one isn't. It should be fine....*should!*

If you dont want to do that you can always upgrade to the latest version of conkyEmail.py from the tarball in the first post, by replacing it in your /usr/share/conkyemail folder.

If that doesn't work I'll take a further look at the unicode support...

---

### Post by detroit/zero on 2009-01-26
> **kaivalagi said:**
> First off can you try using the intrepid repo instead? It is updated whereas the hardy one isn't. It should be fine....*should!*

If you dont want to do that you can always upgrade to the latest version of conkyEmail.py from the tarball in the first post, by replacing it in your /usr/share/conkyemail folder.

If that doesn't work I'll take a further look at the unicode support...
I'll give the Intrepid repo a shot.. I'd hate for you to go and do a bunch of work on my account ;)

---

### Post by kaivalagi on 2009-01-26
> **detroit/zero said:**
> I'll give the Intrepid repo a shot.. I'd hate for you to go and do a bunch of work on my account ;)

The work may already be done...hence the suggestion. I wouldn't wont to do lots of work I already have done ;)

I did some unicode tinkering on all the scripts based on some issues in the google calendar one which were resolved. With all my apps/scripts, anything new is done with packages for the latest stable ubuntu release and not previous ones...otherwise I'd be there all day updating multiple versions of the scripts. SO, currently only intrepid scripts are kept updated....

And in theory though the latest version of the repo can be used with any ubuntu version as it relies mostly on python 2.5...

Hope that works for you

---

### Post by detroit/zero on 2009-01-26
> **kaivalagi said:**
> The work may already be done...hence the suggestion. I wouldn't wont to do lots of work I already have done ;)

I did some unicode tinkering on all the scripts based on some issues in the google calendar one which were resolved. With all my apps/scripts, anything new is done with packages for the latest stable ubuntu release and not previous ones...otherwise I'd be there all day updating multiple versions of the scripts. SO, currently only intrepid scripts are kept updated....

And in theory though the latest version of the repo can be used with any ubuntu version as it relies mostly on python 2.5...

Hope that works for you
No worries.. it worked like a charm.

Thanks for the help!

---

### Post by dccrens on 2009-01-31
Hey kaivalagi!
Hope all is well.. I just got around to installing your script via the repo. I am using it to check gmail POP.

However, it seems to always display the same thing "31" New emails even after I have gone on to gmail and marked everything in the inbox as read. Is this caching somewhere?

I run the script using:

```
${execi 60 conkyEmail --servertype=POP --servername=pop.gmail.com --username=XXXXX --password=XXXXX --ssl --mailinfo=2}
```

The output is:

```
31 New
1. Frank Mehnert: "Re: [vbox-users] Repository for openSUSE Hosts?"
2. Frank Mehnert: "Re: [vbox-users] Announce: VirtualBox 2.1.2 released!"

```

So what am I doing wrong?

Verbose output shows the following:

```
*** INITIAL OPTIONS:
    servertype: POP
    servername: pop.gmail.com
    folder: Inbox
    ssl: True
    username: XXXXX
    password: XXXXXX
    mailinfo: 2
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Logging on to POP server: pop.gmail.com
INFO: Getting message count from POP server: pop.gmail.com
INFO: Extracting message data from POP server "pop.gmail.com"
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Logging off from POP server: pop.gmail.com
31 New
1. Frank Mehnert: "Re: [vbox-users] Repository for openSUSE Hosts?"
2. Frank Mehnert: "Re: [vbox-users] Announce: VirtualBox 2.1.2 released!"

```

Any ideas on this? 

Thanks!

---

### Post by dccrens on 2009-01-31
I figured it out... My gmail account is set for both POP and IMAP... If I switch to IMAP using:

```
${execi 60 conkyEmail --servertype=IMAP --servername=imap.gmail.com --username=XXXXX --password=XXXXX --ssl --mailinfo=2}
```

it works perfectly...

Put me down as another satisfied customer...

---

### Post by Tick-Tock on 2009-02-02
Hi. There are some news about hotmail: now it supports the pop3 protocol.
So I tried to use your script for hotmail, but there is a problem: it return the number of all email in the inbox, not the new only. For example at this time I have 84 readen email and 1 to read, the script return 85 email.
The problem for you is that, as I've read on the internet, the supports about pop3 is available only in some countries, as Australia, Uk, Netherlands, France, Spain, Germany, Japan, Italy and Canada. If anyone can solve this...

[http://www.mydigitallife.info/2009/01/16/hotmail-free-pop3-and-smtp-access-and-server-configuration-settings/](http://www.mydigitallife.info/2009/01/16/hotmail-free-pop3-and-smtp-access-and-server-configuration-settings/)

---

### Post by kaivalagi on 2009-02-02
> **Tick-Tock said:**
> Hi. There are some news about hotmail: now it supports the pop3 protocol.
So I tried to use your script for hotmail, but there is a problem: it return the number of all email in the inbox, not the new only. For example at this time I have 84 readen email and 1 to read, the script return 85 email.
The problem for you is that, as I've read on the internet, the supports about pop3 is available only in some countries, as Australia, Uk, Netherlands, France, Spain, Germany, Japan, Italy and Canada. If anyone can solve this...

[http://www.mydigitallife.info/2009/01/16/hotmail-free-pop3-and-smtp-access-and-server-configuration-settings/](http://www.mydigitallife.info/2009/01/16/hotmail-free-pop3-and-smtp-access-and-server-configuration-settings/)

The short answer is that pop3 is crap, it doesn't support new email only notification unlike imap. The script would have to keep a tab on message id's and manage the counts based on compares etc...that's not going to happen

Just use gmail with imap :)

---

### Post by kaivalagi on 2009-02-02
**[COLOR="Red"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

New instructions on setting up the repository in your system have been added to the first post, as follows

[COLOR="Red"]**Remove any existing /etc/apt/sources.list entry before or after doing this!**[/COLOR]

1) Create the necessary list file for access to the repository by running this:

```
sudo wget -q http://www.kaivalagi.com/m-buck-ppa.list -O /etc/apt/sources.list.d/m-buck-ppa.list
```

2) Add the repository public key to your apt setup by running this:

```
wget -q http://www.kaivalagi.com/m-buck-ppa-key.gpg -O- | sudo apt-key add -
```

---

### Post by nlooije on 2009-03-01
Hi,

Im running your script rather well at the moment, just wondering if there is any possibility to limit the characters in the subject line, or perhaps make the line break and continue on the next line?

This is too hinder conky extending horizontally when someone sends me an email with a subject that is far too long! See the screenshot in the attachment for an idea of what i mean.

Niels

---

### Post by nlooije on 2009-03-01
Hi again,

i barely closed the above post when i found a way to define a maximum window width for corky which took care of it.

ciao,

Niels

---

### Post by kaivalagi on 2009-03-01
> **nlooije said:**
> Hi again,

i barely closed the above post when i found a way to define a maximum window width for corky which took care of it.

ciao,

Niels

Never the less I'll see what I can add to the script to give some options, a maxwidth settings which wraps text might be sensible here...

---

### Post by WiseGuy1020 on 2009-03-05
That thats the only thing missing that I would love to see, a text wrap. 

Maybe add something like this 

#wrap format for subject
$Text::Wrap::columns=65; #Number of columns to wrap subject at
$initial_tab=""; #Tab for first line of subject
$subsequent_tab="\t"; #tab for wrapped lines
$quote="\""; #put quotes around subject

---

### Post by kaivalagi on 2009-03-06
> **WiseGuy1020 said:**
> That thats the only thing missing that I would love to see, a text wrap. 

Maybe add something like this 

#wrap format for subject
$Text::Wrap::columns=65; #Number of columns to wrap subject at
$initial_tab=""; #Tab for first line of subject
$subsequent_tab="\t"; #tab for wrapped lines
$quote="\""; #put quotes around subject

I've added a maxwidth option to the script which uses a wrapping function on the mailinfo output.

I'll get this out in the next couple of days

Attached the py file here for now for you to play with :)

```
 -w NUMBER, --maxwidth=NUMBER
                        [default: 80] Define the number of characters to
                        output per line

```

---

### Post by altonbr on 2009-03-06
Can you start to compile [your PPA]("https://launchpad.net/~m-buck/+archive/ppa") for Jaunty please? :)

---

### Post by kaivalagi on 2009-03-06
> **altonbr said:**
> Can you start to compile [your PPA]("https://launchpad.net/~m-buck/+archive/ppa") for Jaunty please? :)

When I upgrade I will...no point until I have tested on it first. I plan to migrate a week into the final release, not before. Once there and working I'll go through all my ppa packages and upgrade.

You can install using the intrepid ppa as before, it's python based so should work on any OS with python 2.4 or greater....give it a try. There is no compiling, just package generation.

---

### Post by andrewsomething on 2009-03-07
Hey, just tried out you script. Very cool, but I'm seeing massive memory usage after having it running for a few hours. See screenshot. I'm using conkyemail 2.01 on Jaunty.

---

### Post by kaivalagi on 2009-03-07
> **andrewsomething said:**
> Hey, just tried out you script. Very cool, but I'm seeing massive memory usage after having it running for a few hours. See screenshot. I'm using conkyemail 2.01 on Jaunty.

Was this happening on Intrepid?

I have yet to get Jaunty installed, so can't tell whether it is a alpha software issue or not...

I do not get mad memory use like that with any of my python scripts when they run for days...but I am running a full release of Ubuntu not a test one.

All I can say is that I have yet to upgrade to and build packages for Jaunty, so can't really do much about this sort of thing just yet. Once I have switched I can investigate properly but I do suspect it is because Jaunty has a new python version (2.6 something) and this is in it's infancy and has teething problems? the email libs could be buggy etc....

---

### Post by WiseGuy1020 on 2009-03-11
can I just sub your new .py file for the one that came in the repository  to get the --maxwidth option, or do I have to recompile it?
You have not updated it in the repository have you?

---

### Post by kaivalagi on 2009-03-11
> **WiseGuy1020 said:**
> can I just sub your new .py file for the one that came in the repository  to get the --maxwidth option, or do I have to recompile it?
You have not updated it in the repository have you?

Nope, totally forgot...

I assume it works okay for you?

If all is okay with it I'll update in the next couple of days, things are a tad busy right now at work

---

### Post by WiseGuy1020 on 2009-03-11
It works pretty good. Thanks for responding so quickly.

2 things I noticed:  
               
       1. The biggest gripe I have is that wrap brings the second line
       of text all the way to the number of the email. I have illustrated
       this in this paragraph.It would look a lot better IMHO if it lined 
       up like my next paragraph.

       2. Not that big of a deal I guess, but it would be nice if there was 
          an option to make the text at the end of the line hyphenate
          instead of jumping to the next line.  

Anyway thanks very much for these scripts, I use the email,forecast,exaile, and deluge ones. These make my desktop look awesome and cuts down on resources.(do to all the other screenlets and panel apps that I can remove now) 

Keep up the good work :)


edit: I tried to align how I wanted it to look but the forum auto-formats or something
see screenshot attached[ATTACH]106127[/ATTACH]

---

### Post by kaivalagi on 2009-03-11
> **WiseGuy1020 said:**
> It works pretty good. Thanks for responding so quickly.

2 things I noticed

I'll see what I can do about point 1, point 2 might be a bit trickier but we'll see

---

### Post by WiseGuy1020 on 2009-03-11
wow thanks for the pm defintely missed that one. That what I get for smoking and typing :) oh, well new password is no big deal.

---

### Post by kaivalagi on 2009-03-12
> **WiseGuy1020 said:**
> wow thanks for the pm definitely missed that one. That what I get for smoking and typing :) oh, well new password is no big deal.

See attached, it handles point 1, point 2 isn't that straight forward as the textwrap class doesn't support it...

---

### Post by altonbr on 2009-03-12
> **kaivalagi said:**
> When I upgrade I will...no point until I have tested on it first. I plan to migrate a week into the final release, not before. Once there and working I'll go through all my ppa packages and upgrade.

You can install using the intrepid ppa as before, it's python based so should work on any OS with python 2.4 or greater....give it a try. There is no compiling, just package generation.

Just reporting that downloading the Intrepid conkyEmail .deb works perfectly fine in Jaunty.

Thank you :)

---

### Post by WiseGuy1020 on 2009-03-13
That new python file works great.

I thought the hyphen might be difficult. 

Some more suggestions: 

1.Instead of a hyphen could you add a --maxtext option? One that limits how much text is displayed for each email? Sometimes an email like one from my bank has a lot of text in the subject field.

2.The only other thing I can think of is a way to change the colors of the numbers, sender, or subject text of the emails.

Again man great job. Some people at work have seen my desktop and are ridiculously jealous, especially when they see how little resources it uses. I have been directing several people to your threads. People like you are what make open source great!

---

### Post by kaivalagi on 2009-03-13
> **WiseGuy1020 said:**
> That new python file works great.

I thought the hyphen might be difficult. 

Some more suggestions: 

1.Instead of a hyphen could you add a --maxtext option? One that limits how much text is displayed for each email? Sometimes an email like one from my bank has a lot of text in the subject field.

2.The only other thing I can think of is a way to change the colors of the numbers, sender, or subject text of the emails.

Again man great job. Some people at work have seen my desktop and are ridiculously jealous, especially when they see how little resources it uses. I have been directing several people to your threads. People like you are what make open source great!

I'll look into point one, I think we need a switch option called --nowrap, if used with --maxwidth that could accommodate the requirement...

Option 2 is possible but I am not going there, too many options to accommodate for all the possibilities...

I'll post back a new .py in a few days with the --nowrap option so you can play a little before I release :)

---

### Post by kaivalagi on 2009-03-13
@WiseGuy1020

Not quite a few days, I got carried away and finished the changes today...

New help options as follows:

```
  -w NUMBER, --maxwidth=NUMBER
                        [default: 80] Define the number of characters to
                        output per line
  -n, --nowrap          If set stops any text wrapping of mailinfo output, the
                        --maxwidth will set the number of characters for the
                        single line of output
  -q CHAR, --quote=CHAR
                        [default: "] The character to use for quotations
                        around the subject line

```

So if you use --nowrap you will get a single line output, with the length based on the maxwidth setting.

Have a go with the attached and let me know how it goes, I'll roll it out if okay :)

---

### Post by WiseGuy1020 on 2009-03-14
Another suggestion would be the ability to set the number of lines that each email displays. In my screen-shot I would like to set the limit to two lines so the last email's third line does not appear. 

On another note after that last update my conkyForecast is no longer showing barometric pressure. Not sure if that is due to the website, the script, or my conkyrc text_buffer_size. Actually I should be posting this on the forecast thread....

Oh and thanks once again.

---

### Post by kaivalagi on 2009-03-14
> **WiseGuy1020 said:**
> Another suggestion would be the ability to set the number of lines that each email displays. In my screen-shot I would like to set the limit to two lines so the last email's third line does not appear. 

On another note after that last update my conkyForecast is no longer showing barometric pressure. Not sure if that is due to the website, the script, or my conkyrc text_buffer_size. Actually I should be posting this on the forecast thread....

Oh and thanks once again.

Good call, I'll remove the --nowrap option and create a --linelimit option instead, shouldn't be too much bother. Set to 1 it should cause the same affect as currently (minus the ..)

No changes in conkyForecast that should affect the barometric pressure output...post on that thread anyway as someone might be able to help there...

---

### Post by kaivalagi on 2009-03-14
New version again, this time with --linelimit option instead of --nowrap

```
  -w NUMBER, --maxwidth=NUMBER
                        [default: 80] Define the number of characters to
                        output per line
  -l NUMBER, --linelimit=NUMBER
                        [default: 0] If above zero this limits the number of
                        lines output for mail info
  -q CHAR, --quote=CHAR
                        [default: "] The character to use for quotations
                        around the subject line

```

As before I'll release when you're happy...hopefully this is it :)

---

### Post by WiseGuy1020 on 2009-03-14
Works perfectly! 

Yeah I don't see any other improvement thats needed. Except the color but I understand why that would be difficult. IMHO this update is ready to rock.

Thanks a lot for your work. This is the first time I have ever really had any input on the design of any software, short of an electronic equivalent of a card in a comment box. I find it amazing that my advice was even heeded, much more the speed in which it was. 

Keep up the good work and I am greatly interested to see what you come up with next. :)

p.s. the weather script is working fine after a reload, must have been the site.

---

### Post by kaivalagi on 2009-03-15
This is a hobby so I like to tinker when I get a chance, if you can think of any new functionality that might be useful just speak up...that includes brand new scripts.

I am not saying I'll do it but I would appreciate any bright ideas...

I am trying to build up a set of functionality in my gtk app (see sig)

I'll have the conkyEmail updates released at some point soon

Cheers

---

### Post by kaivalagi on 2009-03-15
**[COLOR="DarkOrange"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Added a couple of new options, --maxwidth and --linelimit, change details can be found here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkyemail_2.04_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkyemail_2.04_source.changes)

The first post has been updated and the apt package should be available soon

Cheers

---

### Post by WiseGuy1020 on 2009-03-16
Each time you release a new python file for testing I have to go back in and add 993 to the "imap = imaplib.IMAP4_SSL(servername)" line. 

I was wondering if adding the --port option had proved to difficult or if you just had not yet got around to it. Or did you just forget? :)

No big deal it is very easy to hack the python file, but I think it would be a nice option to add.

As always thanks alot.

---

### Post by kaivalagi on 2009-03-16
> **WiseGuy1020 said:**
> Each time you release a new python file for testing I have to go back in and add 993 to the "imap = imaplib.IMAP4_SSL(servername)" line. 

I was wondering if adding the --port option had proved to difficult or if you just had not yet got around to it. Or did you just forget? :)

Yep, forgot...all these requests need to be logged somewhere like how I handle changes at work but that sounds too much like work and not play!

> **WiseGuy1020 said:**
> No big deal it is very easy to hack the python file, but I think it would be a nice option to add.

Edited to handle a port option in less time than it's taken to write this post :) Let's hope it works...

You should be able to either call the script using the --port option or use something like below inside your existing [] in your template:

```
--port=993
```

New option is this:

```
  -o NUMBER, --port=NUMBER
                        Define an alternative port number to use other than
                        the default for the protocol/ssl
```

New script attached...

Now is there anything else I've forgotten before I release another version ;)

---

### Post by WiseGuy1020 on 2009-03-16
I am getting an error using that new script. See screen-shot.


And I'm sure I'll only come up with something after you release it. :)

---

### Post by kaivalagi on 2009-03-16
> **WiseGuy1020 said:**
> I am getting an error using that new script. See screen-shot.
Give my previous posts attachment a try, just updated it...

> **WiseGuy1020 said:**
> And I'm sure I'll only come up with something after you release it. :)

Don't I know it! ;)

---

### Post by WiseGuy1020 on 2009-03-16
Sweet!

Works perfectly.

I have been trying hard to think of something else. The only thing else I can think of is a way to display a PGP encrypted email's sender and subject text. Like an option where you could set the path to where your key file is and your password. 

Ideally the best would be a way for conky to prompt your for your password when your script detects an encrypted email. I would not want to keep my PGP password in a conkyrc file. The usage would be like the enigmail extension for Thunderbird. 

I realize this might require some hefty coding, if it is even possible.

Cheers! :)

---

### Post by kaivalagi on 2009-03-16
> **WiseGuy1020 said:**
> Sweet!

Works perfectly.

I have been trying hard to think of something else. The only thing else I can think of is a way to display a PGP encrypted email's sender and subject text. Like an option where you could set the path to where your key file is and your password. 

Ideally the best would be a way for conky to prompt your for your password when your script detects an encrypted email. I would not want to keep my PGP password in a conkyrc file. The usage would be like the enigmail extension for Thunderbird. 

I realize this might require some hefty coding, if it is even possible.

Cheers! :)

Can't get feedback with conky, and to be honest that functionality would be a nightmare to develop...I'll release what we have right now :)

---

### Post by kaivalagi on 2009-03-16
**[COLOR="DarkOrange"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Added --port option, change details can be found here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkyemail_2.05_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkyemail_2.05_source.changes)

The first post has been updated and the apt package should be available soon

Cheers

---

### Post by WiseGuy1020 on 2009-03-16
Yeah I guessed that would be a royal pain to implement. Short of that I can't come up with any other features I would want. 

Still amazed at the quick turnaround time. 

Thanks. :)

---

### Post by kaivalagi on 2009-03-16
> **WiseGuy1020 said:**
> Yeah I guessed that would be a royal pain to implement. Short of that I can't come up with any other features I would want. 

Still amazed at the quick turnaround time. 

Thanks. :)

Got it nailed, I can debug my scripts with ease (eclipse and pydev) and I have scripts to build and deploy any script/app onto my machine for package testing. I then upload the source package when happy to launchpad, which results in a apt package update :)

Works really well...

---

### Post by Bruce M. on 2009-03-17
Am I the only one that only wants to know **[COLOR="Blue"]"if"[/COLOR]** I have mail or not?

This part of the app has never failed me: 0 or a number for both mail boxes.

In fact it would be nice if the app could "tell you"

if x = 0 output "no"
else
output "yes"

and somewhere in the config file, an area to modify the screen output:

yes="It's gotta be spam!"
no="No one loves you!"

Imagine, you could then make a script that rotates different responses.  :)

yes="You must owe them money?"
yes="Quick, read it before it melts!"
no="Not even close!"
no="In your dreams!"

Have a nice day.
Bruce

---

### Post by snkiz on 2009-03-24
I'm having a little trouble with the script, I had it working fine then one day couple weeks ago it just quit, nothing changed far as I know, but no more email :( here are my screen shots and template file:

```
${font Terminus:style=Bold:size=9}Google: ${font}[--servertype=IMAP --servername=imap.gmail.com --ssl --port=993 --username=myname --password=mypassword --mailinfo=3]
```]

note just tried to add the port option.. no help.

---

### Post by WiseGuy1020 on 2009-03-25
Yeah I am getting the same error.

---

### Post by kaivalagi on 2009-03-25
I'll take a look at the weekend, I'm away from home on training at the mo

---

### Post by paulus4605 on 2009-03-29
kaivalagi,
is there a way to shorten the output of the subjectline?
meaning if you have a mail from example :kaivalagi with subject "I really want to know how your weekend was" 
the risk is that your conky is getting bigger to get the complete subject on 1 line in your conky.
is there a way to limit it to lets say 20 characters?
thanks 

Paul

---

### Post by kaivalagi on 2009-03-29
> **paulus4605 said:**
> kaivalagi,
is there a way to shorten the output of the subjectline?
meaning if you have a mail from example :kaivalagi with subject "I really want to know how your weekend was" 
the risk is that your conky is getting bigger to get the complete subject on 1 line in your conky.
is there a way to limit it to lets say 20 characters?
thanks 

Paul

Yep, I added some options not so long ago for just that, see the post here: [http://ubuntuforums.org/showpost.php?p=6897677&postcount=207](http://ubuntuforums.org/showpost.php?p=6897677&postcount=207)

I think setting --maxwidth to 20 and --linelimit to 1 would do it.

Run the help for more details, e.g.:

```
conkyEmail -h
```

Hope that helps

btw, how was your weekend? :)

---

### Post by snkiz on 2009-03-29
> **kaivalagi said:**
> I'll take a look at the weekend, I'm away from home on training at the mo

have you had a chance to look at it yet? not to be a pest :)

---

### Post by kaivalagi on 2009-03-29
> **snkiz said:**
> have you had a chance to look at it yet? not to be a pest :)

Sorry, I haven't...I've spend most of my time since then away from home on a course and haven't had access to my PC. Thanks for reminding me though ;)

I think (but can't be certain) that the issue is happening when trying to sort the email info list, when comparing a message with a good datetime against a message without one. This shouldn't happen but has somehow...

For me to figure the problem out better (this doesn't happen for me with 5 different email providers) I need you to replace the script with the one attached so I get more error trace info.

To replace it, extract the tarball attached somewhere and run this:

```
sudo cp **[COLOR="Red"]/path/to/new/[/COLOR]**conkyEmail.py /usr/share/conkyemail/conkyEmail.py
```

Make sure you replace the red text with the right path to the new script...

Once you've replaced the script, run you're conky from the terminal again and paste the error here.

---

### Post by snkiz on 2009-03-30
> **kaivalagi said:**
> Once you've replaced the script, run you're conky from the terminal again and paste the error here.
 done, not much output though:

```
ERROR: getOutputData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 135, in getOutputData
    self.emaillist.sort(reverse=True)
  File "/usr/share/conkyemail/conkyEmail.py", line 85, in __cmp__
    return cmp(self.recvdate, other.recvdate)
TypeError: can't compare datetime.datetime to NoneType

```

I should note this doesn't happen with yahoo just gmail

---

### Post by kaivalagi on 2009-03-30
> **snkiz said:**
> done, not much output though:

```
ERROR: getOutputData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 135, in getOutputData
    self.emaillist.sort(reverse=True)
  File "/usr/share/conkyemail/conkyEmail.py", line 85, in __cmp__
    return cmp(self.recvdate, other.recvdate)
TypeError: can't compare datetime.datetime to NoneType

```

I should note this doesn't happen with yahoo just gmail

We now have line numbers :)

Well I still can't understand why this error is happening as the problem is caused by something that shouldn't happen. But it obviously does happen so I have applied a belt and braces approach and the script should now handle sorting when no recvdate is present.

Can you give the attached a try, if this works I'll rollout a new version of the script soon(ish) after.

---

### Post by uldo on 2009-03-30
I got a problem... Everything that goes after any IMAP doesnt shows up (as u can see in attached pict).... Tried --verbose and everything goes just fine :/ (on all of them)
If i move IMAP before POP, than the pop disapears...
**[color=red][SIZE="6"]EDIT:[/SIZE]**[/color] false alarm... found my mistake... "text_buffer_size 256" was too short :D
This is my conkyemail.template:
```
    ${voffset 10}${color DimGray}xxxx@inbox.lv: ${font}${color1}[--servertype=POP --servername=pop.inbox.lv --username=xxx --password=xxx --mailinfo=3]
    ${voffset 10}${color DimGray}xxxxxx@gmail.com: ${font}${color1}[--servertype=IMAP --servername=imap.gmail.com --ssl --username=xxx --password=xxx --mailinfo=3]
    ${voffset 10}${color DimGray}xxx@xxx.lv: ${font}${color1}[--servertype=IMAP --servername=xxx.net --port=993 --ssl --username=xxx@xxx.lv --password=xxxxx --mailinfo=3]
    ${voffset 10}${color DimGray}xxx@aizmirsti.lv: ${font}${color1}[--servertype=POP --servername=mail.aizmirsti.lv --username=xxxx --password=xxxx --mailinfo=3]
```

conkymain:
```
background yes
    use_xft yes
    xftfont 123:size=8
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 250 5
    maximum_width 400
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color gray
    default_shade_color red
    default_outline_color green
    alignment top_right
    gap_x 10
    gap_y 10
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 2
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 256

*lots of other stuff*

${execpi 600 conkyEmail --template=/home/uldo/Programs/Conky/conkyemail.template}
```

With verbose:
```
$ conkyEmail --servertype=IMAP --servername=xxx.net --port=993 --ssl --username=xxx@xxx.lv --password=xxx --mailinfo=3 -v
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: xxx.net
    port: 993
    folder: Inbox
    ssl: True
    username: xxx@xxx.lv
    password: xxx
    template: None
    mailinfo: 3
    maxwidth: 80
    linelimit: 0
    quote: "
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Logging on to IMAP server: xxx.net
INFO: Searching for new mail on IMAP server "xxx.net" in folder "Inbox"
INFO: Logging of from IMAP server: xxx.net
0

```

any ideas or is it a bug?

---

### Post by kaivalagi on 2009-03-31
Easy mistake to make :)

---

### Post by snkiz on 2009-03-31
Success! :D:D your a god I sacrifice my xp partition to you!

---

### Post by Bruce M. on 2009-03-31
> **snkiz said:**
> Success! :D:D your a god I sacrifice my xp partition to you!

I always like a success story! And from a Canuck too! Even better. :D

But, I'm not sure I'd go so far as to say he's a god!
[SIZE="1"]{background rumblings from K: "Shut up Bruce!"}[/SIZE]
OK, so he gets the xp partition ... can I have the background?

In other words: where did you get that background?

Have a nice day.
Bruce

---

### Post by snkiz on 2009-03-31
> **Bruce M. said:**
> I always like a success story! And from a Canuck too! Even better. :D

But, I'm not sure I'd go so far as to say he's a god!
[SIZE="1"]{background rumblings from K: "Shut up Bruce!"}[/SIZE]
OK, so he gets the xp partition ... can I have the background?

In other words: where did you get that background?

Have a nice day.
Bruce

I threw a copy of crunchbang on a separate partition cuz I burned out a stick of ram and gnome wasn't happy about that. It came with it but I think I've seen it on gnome-look to. The rest of the specs are:
conky=   conkycolors (if options removed)/crunch default/k's weather default modified
gtk=     midnight-future(not released) mix of midnight black plastic and future with a lot of custom work thrown in
openbox= onyx comes with openbox themes
icons=   Hydroxygen

I'm honored you asked your name carries wieght around here too. ):P

---

### Post by Bruce M. on 2009-03-31
> **snkiz said:**
> I threw a copy of crunchbang on a separate partition cuz I burned out a stick of ram and gnome wasn't happy about that.

OK, so I gotta get crunchbang. Unless I could convince a fellow Canuck to put it some place like ... oh, I donno ... Imageshack maybe. ;)

> **snkiz said:**
> I'm honored you asked your name carries wieght around here too. ):P

Now see, that's where you're confused. It's not my name, it's my stomach. ):P back at ya.

Have a nice day.
Bruce

---

### Post by snkiz on 2009-03-31
> **Bruce M. said:**
> OK, so I gotta get crunchbang. Unless I could convince a fellow Canuck to put it some place like ... oh, I donno ... Imageshack maybe. ;)
Bruce

will google do? 
[http://picasaweb.google.com/snkiz1.0/WhereDidYouGetThat?feat=directlink]("http://picasaweb.google.com/snkiz1.0/WhereDidYouGetThat?feat=directlink")

---

### Post by Bruce M. on 2009-03-31
> **snkiz said:**
> will google do? 
[http://picasaweb.google.com/snkiz1.0/WhereDidYouGetThat?feat=directlink]("http://picasaweb.google.com/snkiz1.0/WhereDidYouGetThat?feat=directlink")

OH! Absolutely. Thanks.

BTW, I answered an un-answered post of yours, from last January. :)

And it's not just the first two, the third one works as well.
(I tested it, my first ever addition of that type.)

Now, lets see if you can find it. :-\"

${color bad}Me$color

CHIMO!
Bruce

---

### Post by snkiz on 2009-04-03
K, got another problem I think. My wife is using yahoo and the script is showing everything in her inbox even though its all been marked read. Or is that the limitation of POP access?

---

### Post by kaivalagi on 2009-04-03
> **snkiz said:**
> K, got another problem I think. My wife is using yahoo and the script is showing everything in her inbox even though its all been marked read. Or is that the limitation of POP access?

You guessed right, the pop protocol has no method of identifying mail as read or not. The only thing you can do is setup the mail account to NOT keep the mail on the server, i.e. uncheck the keep mail on server options etc

I really do not understand why any providers use pop any more, imap is just as easy to setup and is far more feature rich.

Unfortunately yahoo doesn't provide an imap interface :(

---

### Post by snkiz on 2009-04-03
Thanks thats what i figured. I dropped yahoo last year never been happier. 
B.T.W I think I figured out why that error was happening. I had a spam message in my inbox that was post-dated, how that helps to get through the filters I don't know, but I does. Its the first time I've seen that in my Google account but used to happen all the time in yahoo.

---

### Post by kaivalagi on 2009-04-03
> **snkiz said:**
> Thanks thats what i figured. I dropped yahoo last year never been happier. 
B.T.W I think I figured out why that error was happening. I had a spam message in my inbox that was post-dated, how that helps to get through the filters I don't know, but I does. Its the first time I've seen that in my Google account but used to happen all the time in yahoo.

If you are willing, I'd like to see the mail headers for that email, you might want to remove your email address of course. The easiest way to view them in Thunderbird is to open the email and goto View->Headers->All and take a screenshot

What I am really after is the received date lines

---

### Post by wmsheep on 2009-04-08
Hi all

OK, so I`m having a go at this IMAP thing on conky to get my uni mail, but all I`m getting in my conky panel is a nice little "?"

for some reason I`m also getting this output

```
ERROR: getPOPEmailData:Unexpected error:-ERR [AUTH] Error logging in. Please visit http://mail.yahoo.com
```

my template file is as follows

```

${voffset 10}${font Terminus:style=Bold:size=9}${color3}Uni: ${font}${color1}[--servertype=IMAP --servername=imap4.XXXX.ac.uk --ssl --port=993 --username=ad\ZZZZ --password=YYYYYYYYYY --mailinfo=3]

```


the "ad\" characters in the user name are put there by the uni.


any idea where I`m going wrong??

Ta

Mark

---

### Post by snkiz on 2009-04-09
> **wmsheep said:**
> Hi all

OK, so I`m having a go at this IMAP thing on conky to get my uni mail, but all I`m getting in my conky panel is a nice little "?"

for some reason I`m also getting this output

```
ERROR: getPOPEmailData:Unexpected error:-ERR [AUTH] Error logging in. Please visit http://mail.yahoo.com
```


yahoo doesn't do IMAP. your error says get POP email data. Change your server to POP3 and yahoo's default port um... 443 I think

---

### Post by kaivalagi on 2009-04-09
> **wmsheep said:**
> Hi all

OK, so I`m having a go at this IMAP thing on conky to get my uni mail, but all I`m getting in my conky panel is a nice little "?"

for some reason I`m also getting this output

```
ERROR: getPOPEmailData:Unexpected error:-ERR [AUTH] Error logging in. Please visit http://mail.yahoo.com
```

my template file is as follows

```

${voffset 10}${font Terminus:style=Bold:size=9}${color3}Uni: ${font}${color1}[--servertype=IMAP --servername=imap4.XXXX.ac.uk --ssl --port=993 --username=ad\ZZZZ --password=YYYYYYYYYY --mailinfo=3]

```


the "ad\" characters in the user name are put there by the uni.


any idea where I`m going wrong??

Ta

Mark

Either what snkiz has said or you are pointing to a different template by mistake in your conkyrc.

Start by trying this in the terminal:

```
conkyEmail --servertype=IMAP --servername=imap4.XXXX.ac.uk --ssl --port=993 --username=ad\ZZZZ --password=YYYYYYYYYY --mailinfo=3
```

If that works then get busy with the conkyrc and template to suit

Hope that helps

---

### Post by wmsheep on 2009-04-09
> **kaivalagi said:**
> Either what snkiz has said or you are pointing to a different template by mistake in your conkyrc.

Start by trying this in the terminal:

```
conkyEmail --servertype=IMAP --servername=imap4.XXXX.ac.uk --ssl --port=993 --username=ad\ZZZZ --password=YYYYYYYYYY --mailinfo=3
```

If that works then get busy with the conkyrc and template to suit

Hope that helps

YAY, thanks.

Got it to work, and I could see where I was making the errors.

Many thanks.

Mark

---

### Post by snkiz on 2009-04-12
hey kaivalagi I have a request, I'd like to try my hand a writing a bash script to fill in the variables for your scripts. I'm going to submit to Crunchbang when its done. Anyway I thought it would be handy if an unconfigured or erroneous script could display a message like "Please configure ConkyXxx (insert script name). I'm sure I'll be back to pick your brain as I go. Also, and I do apologize for cramming to thought in one post or getting off topic, Do you know if conky can call other config files for inclusion Similar to a gtkrc? (ie: include mainrc) If you wanna start a new thread or know of one that exists feel free to point me in the right direction. ;)

---

### Post by kaivalagi on 2009-04-12
> **snkiz said:**
> hey kaivalagi I have a request, I'd like to try my hand a writing a bash script to fill in the variables for your scripts. I'm going to submit to Crunchbang when its done. Anyway I thought it would be handy if an unconfigured or erroneous script could display a message like "Please configure ConkyXxx (insert script name). I'm sure I'll be back to pick your brain as I go. Also, and I do apologize for cramming to thought in one post or getting off topic, Do you know if conky can call other config files for inclusion Similar to a gtkrc? (ie: include mainrc) If you wanna start a new thread or know of one that exists feel free to point me in the right direction. ;)

That's great, create some conkyrc and templates and publish them by all means, the more the merrier!

I will not suggest in error messages that the use of a script outside of the package is a good idea though, I'd also be siding with one author/publication. By all means if you want to contribute to example scripts then go ahead, I'll ad them to the package if any good and you can reference them.

conky only supports one rc file at a time...I am not sure I can help any more?

---

### Post by History35453 on 2009-04-14
I have the error "ERROR: getOutputData:Unexpected error:can't compare datetime.datetime to NoneType" 

I have the Version conkyEmail v.2.05 and Ubuntu Jaunty Jackalope. 

MY conky Config:

TEXT
${font}${color}${goto 5}UPLOAD${color1}${upspeed wlan0}kb/s (${totalup wlan0}) ${color}DOWNLOAD${color1}${downspeed wlan0}kb/s (${totaldown wlan0})${alignr} ${color}
${font}${color}${goto 5}${time %H:%M}${goto 45}CPU${color1}${cpu cpu}%${goto 100}${color}RAM${color1}${memperc}% ${color}IP${color1}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}${goto 270}${color}WETTER${color1}${execi 1800 conkyForecast --locale=de -l GMXX0117 --datatype=CT | awk '{print toupper($_);}' } ${color}TEMP${color1}${execi 1800 conkyForecast -l GMXX0117 --hideunits -x --datatype=HT}'C ${color}WIND${color1}${execi 1800 conkyForecast --locale=de -l GMXX0117 --datatype=WS} (${execi 1800 conkyForecast --location=GMXX0117 --datatype=WD})   ${color}ROOT${color1}${fs_used_perc /}% ${color}${color1}${execi 1800 aptitude search "~U" | wc -l | tail} Updates!!!${color}
${color4}${font Terminus:style=Bold:size=14}@ 

Here is the line for conkyEmail

${font Terminus:style=Bold:size=11}EMail${font}${voffset 5}${alignr}${color4}${font Terminus:style=Bold:size=9} GMX Mail POP SSL:  ${color1}${font}${execi 600 conkyEmail --servertype=POP --servername=pop.gmx.net --username=XXXXXXXXX --password=XXXXXXXX --ssl --mailinfo=4}

---

### Post by kaivalagi on 2009-04-14
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

**I thought I should update the package now as several of you are having the same issues with date received based sorting...**

Added extra error tracing and sorted out date received sort error, change details can be found here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkyemail_2.06_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkyemail_2.06_source.changes)

The first post has been updated and the apt package should be available soon

Cheers

---

### Post by History35453 on 2009-04-14
ohh thanks i'm going to try it out

//edit

ok proplem is fixed. Thanks for your work. 

Is it normal for the building of Conky so long > 1 minute? Could it be that conkyEmail check 1101 Emails ?

This is the output with the option mailinfo=2:

1101 New << this is because pop protocol 

But the first Email is not valid

1.None: ""
2.History35453: "Test"

---

### Post by Bruce M. on 2009-04-14
Hi Folks.

Well it's official, [Conky Hardcore!]("http://conky.linux-hardcore.com/") is open for business. Keep in mind, it's young, under-development and we still have a lot of work to do on it. I personal have a ton of material I have to put up and I know uncertain has a lot more.

Unless uncertain and I specifically state that the work is ours, all information has been gathered from various forums. Of which this thread is the biggest contributor. Many other "forums" direct their conky requests right here, to this specific thread, so it is understandable as to why.

Our "Welcome to Conky Hardcore!" message:

> We’re putting together an encyclopaedia of sorts - dedicated to the Conky system monitor and all the tricks you can make it do. Long have we all wished that there was one place where we could go to find out what we needed to know about Conky and how to make it do what we want. Over time, you’re going to see this grow into that place.

For now, since both your hosts (Bruce & Uncertain) primarily use Debian based systems, this is going to be a little bit Debian-centric. Rest assured, we’ve spent a fair amount of time combing the Conky-threads in Arch, OpenSuse, Fedora, Gentoo, DreamLinux, Ubuntu and other forums, all in the spirit of making this the most complete repository of Conky knowledge around.

What this is not going to be is a help line. People writing comments and emails that contain the phrases, *“How do I …”* or, *“Can someone tell me how to …”* will either be redirected to the various forum threads where all that sort of discussion takes place, *or be ignored/deleted*. Our first priority is to gather the information to put here so you have that “one place” to come to. After all there are Conky threads in most Linux Forums, duplicating those types of threads here will result in this “encyclopaedia” of ideas and samples of how to do things with Conky loosing it’s value as people will have to wade through hundreds of posts to get what they want.

What this is going to be is a place to collect screen shots, scripts, example configurations (from the simple to the obscene), and a showcase for some of the more unique, artistic and creative configurations we’ve seen. We’re going to provide all the above, plus links to even more resources so that everybody from the total “newbie” to the veterans can come here and find something useful.

Unfortunately, when putting together a collection of information like this, with all these different sources, it’s not always possible to credit the original author for their work. Generally, if either of us knows for sure where a script or piece of code came from, that person will be duly credited. If any doubts or uncertainty (or general lack of information) exist as to who may have been the original innovator behind a particular idea, we will leave it uncredited. If you want to claim something we’re displaying as your work, just drop us a line and provide a link to a forum or blog post that shows where and when you came up with the idea, and we’ll see what we can work out.

If you have a new or different way of doing something you see displayed, have a fresh or unique Conky configuration you’d like to share with the world, or have links to other resources that we may have missed, please drop us a line and pass it along.

We hope you enjoy the site!
Bruce & Uncertain

Have a nice day, conkistadors
Bruce

---

### Post by kaivalagi on 2009-04-15
> **History35453 said:**
> ohh thanks i'm going to try it out

//edit

ok proplem is fixed. Thanks for your work. 

Is it normal for the building of Conky so long > 1 minute? Could it be that conkyEmail check 1101 Emails ?

This is the output with the option mailinfo=2:

1101 New << this is because pop protocol 

But the first Email is not valid

1.None: ""
2.History35453: "Test"

Oh dear, yes that will slow things up considerably...

If you have your email server settings defined so that nothing is kept on the server when you retrieve emails that will sort it out, or use imap based email instead.

When I have more time I'll see if I can refactor the code to not do so much but the main problem is because you are using pop and you have so many emails on the server.

---

### Post by kaivalagi on 2009-04-18
**[COLOR="Green"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

**PPA Location Changes**

I have created new PPA's on launchpad to sub-divide all my scripts into their own categories. As such the installation steps for conky scripts have changed, which have been updated on the first post.

You should all change the repository details using the first post steps to get new updates, no new updates will be applied to the old archive location going forwards.

By all means leave the old settings in place too, but these will not help you much.

**Jaunty Package Support**

I have created equivalent packages for Jaunty Jackalope in my PPA's now. They are identical to the intrepid packages but sit under a jaunty location. In my limited testing they all seem to work fine. Again the first post has been updated to describe the setup steps.

Chimo!

---

### Post by fiddler616 on 2009-04-26
I just started using CrunchBang, which comes with conky up and running out of the box. This inspired me to start using conky--and by sheer coincidence, Lifehacker had an article about it recently, with a link to an article with a link here.
So I have the following in my .conkyrc:
```

{execi 1800 conkyEmail --servertype=IMAP --servername=imap.gmail.com --port=993 --ssl --username=tsmacdonald@gmail.com --password=*letmein* --mailinfo=4 --linelimit=3 --connectiontimeout=15}
```
And conky just shows that--literally ("{execi...")
I tried running it in a terminal, and got this:
```
timmy@agamemnon-crunchbang:~$ conkyEmail --servertype=IMAP --servername=imap.gmail.com --port=933 --username=tsmacdonald --password=letmein --mailinfo=4 --linelimit=3 --connectiontimeout=**15**
ERROR: getIMAPEmailData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 403, in getIMAPEmailData
    imap = imaplib.IMAP4(servername, port)
  File "/usr/lib/python2.5/imaplib.py", line 163, in __init__
    self.open(host, port)
  File "/usr/lib/python2.5/imaplib.py", line 230, in open
    self.sock.connect((host, port))
  File "<string>", line 1, in connect
timeout: timed out

?
timmy@agamemnon-crunchbang:~$ conkyEmail --servertype=IMAP --servername=imap.gmail.com --port=993 **--ssl** --username=tsmacdonald@**gmail.com** --password=letmein --mailinfo=4 --linelimit=3 --connectiontimeout=**5**
0

```

What mistake am I making?

Thanks.

---

### Post by Bruce M. on 2009-04-26
Hi fiddler616,

Yea, a lot of places including various distros in their proper forums are linking to or recommending this thread at UF. It seems to be the mega Conky thread of all time. There are a few other Arch users here as well.

Welcome to Conky!

> **fiddler616 said:**
> I just started using CrunchBang, which comes with conky up and running out of the box. This inspired me to start using conky--and by sheer coincidence, Lifehacker had an article about it recently, with a link to an article with a link here.

So I have the following in my .conkyrc:
```
{execi 1800 conkyEmail --servertype=IMAP --serv
```

What mistake am I making?

Thanks.

Ummmmmmmm try putting a $ before the line:
```
${execi 1800 conkyEmail --servertype=IMAP --serv
```

That should work.
Have a nice day.
Bruce

---

### Post by fiddler616 on 2009-04-26
> **Bruce M. said:**
> 
Ummmmmmmm try putting a $ before the line:

Oh wow...thanks...that'll do it. Now I'll never forget a $ in conky for the rest of my life :) 
And I guess the '0' is an unread count? I might need to edit the source to make it '0 new'...

---

### Post by Bruce M. on 2009-04-26
> **fiddler616 said:**
> Oh wow...thanks...that'll do it. Now I'll never forget a $ in conky for the rest of my life :) 
And I guess the '0' is an unread count? I might need to edit the source to make it '0 new'...

Yea, that 0 is probably for 0 new.  :)
Here's my line for two accounts:

```
${voffset -33}${alignc}${color6}Hay  ${color8}${execi 10 conkyEmail --servertype=POP --servername=somewhere.com --username=me_I_think --password=yabbadabbado} ~ ${execi 60 conkyEmail --servertype=POP --servername=pop3.overtherainbow.com --username=gold_pot --password=TOPSECRET}  ${color6}E-mail(s)$color${font}
```

The only thing I want is the count 0 for none and a # for new.
Subject, From etc I get when I open my mail program.  :)

*Yoda: Use the $ fiddler!*
Have a nice day.
Bruce

---

### Post by mike0020 on 2009-05-09
I don't understand how I should go about adding an email (and having it show up for that matter). Can someone please tell me what I should do if I want to add a gmail account and have it displayed in Conky. 

Also is it possible to have multiple email accounts in Conky? Let's say I have 3 new messages in [email]account1@gmail.com[/email] and 2 new messages on [email]account2@gmail.com[/email], is Conky able to tell me that I have 5 new messages in total?

---

### Post by fiddler616 on 2009-05-09
> **mike0020 said:**
> I don't understand how I should go about adding an email (and having it show up for that matter). Can someone please tell me what I should do if I want to add a gmail account and have it displayed in Conky. 

Also is it possible to have multiple email accounts in Conky? Let's say I have 3 new messages in [email]account1@gmail.com[/email] and 2 new messages on [email]account2@gmail.com[/email], is Conky able to tell me that I have 5 new messages in total?
Open up your .conkyrc, and paste this in:
```
${execi 1800 conkyEmail --servertype=IMAP --servername=imap.gmail.com --port=993 --ssl --username=**yourAddress**@gmail.com --password=**yourPassword** --mailinfo=4 --linelimit=3 --connectiontimeout=15}
```
(change the bolded parts to match what you want).

I don't think the Python script supports two separate accounts n atively, but if you're polite you could probably get a bash guy to code you a script that runs conkyEmail.py twice (once for each account), and displays the sum of its output. I don't know if there's a more elegant solution.

Of course, you could just run conkyEmail.py twice from you .conkyrc, and deal with two numbers, but I realize that's not exactly what you want.

---

### Post by mike0020 on 2009-05-10
> **fiddler616 said:**
> Open up your .conkyrc, and paste this in:
```
${execi 1800 conkyEmail --servertype=IMAP --servername=imap.gmail.com --port=993 --ssl --username=**yourAddress**@gmail.com --password=**yourPassword** --mailinfo=4 --linelimit=3 --connectiontimeout=15}
```
(change the bolded parts to match what you want).

I don't think the Python script supports two separate accounts n atively, but if you're polite you could probably get a bash guy to code you a script that runs conkyEmail.py twice (once for each account), and displays the sum of its output. I don't know if there's a more elegant solution.

Of course, you could just run conkyEmail.py twice from you .conkyrc, and deal with two numbers, but I realize that's not exactly what you want.

I was able to get the emails to show, thanks :). Unfortunately I still can't get multiple emails all together, hopefully someone will come around with something that works for that in the near future.

---

### Post by kaivalagi on 2009-05-10
> **mike0020 said:**
> I was able to get the emails to show, thanks :). Unfortunately I still can't get multiple emails all together, hopefully someone will come around with something that works for that in the near future.

You can either exec the script more than once from your conkyrc with different account details to check, or you can use a template which can define multiple account output.

If you take a look at the example conkyrc and template in "/usr/share/conkyemail/example/" you should see the various ways the script can be used. In the example conkyrc there is a template based call and separate execs for both a gmail and a yahoo account.

---

### Post by .salo on 2009-06-12
> **fiddler616 said:**
> I just started using CrunchBang, which comes with conky up and running out of the box. This inspired me to start using conky--and by sheer coincidence, Lifehacker had an article about it recently, with a link to an article with a link here.
So I have the following in my .conkyrc:
```

{execi 1800 conkyEmail --servertype=IMAP --servername=imap.gmail.com --port=993 --ssl --username=tsmacdonald@gmail.com --password=*letmein* --mailinfo=4 --linelimit=3 --connectiontimeout=15}
```And conky just shows that--literally ("{execi...")
I tried running it in a terminal, and got this:
```
timmy@agamemnon-crunchbang:~$ conkyEmail --servertype=IMAP --servername=imap.gmail.com --port=933 --username=tsmacdonald --password=letmein --mailinfo=4 --linelimit=3 --connectiontimeout=**15**
ERROR: getIMAPEmailData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 403, in getIMAPEmailData
    imap = imaplib.IMAP4(servername, port)
  File "/usr/lib/python2.5/imaplib.py", line 163, in __init__
    self.open(host, port)
  File "/usr/lib/python2.5/imaplib.py", line 230, in open
    self.sock.connect((host, port))
  File "<string>", line 1, in connect
timeout: timed out

?
timmy@agamemnon-crunchbang:~$ conkyEmail --servertype=IMAP --servername=imap.gmail.com --port=993 **--ssl** --username=tsmacdonald@**gmail.com** --password=letmein --mailinfo=4 --linelimit=3 --connectiontimeout=**5**
0

```What mistake am I making?

Thanks.


I have same problem. Why I see error (the errors is the same) when start conkyEmail directly from console? 

P.S. I have '$' characters in my password. Can it be a reason of error? If so, how to escape this symbol?

---

### Post by fiddler616 on 2009-06-12
> **.salo said:**
> I have same problem. Why I see error (the errors is the same) when start conkyEmail directly from console? 

P.S. I have '$' characters in my password. Can it be a reason of error? If so, how to escape this symbol?
Well I found my mistakes off the bat, this works from the terminal:
```
timmy@agamemnon-crunchbang:~$ conkyEmail --servertype=IMAP --servername=imap.gmail.com --port=993 **--ssl **--username=tsmacdonald**@gmail.com** --password=letmein --mailinfo=4 --linelimit=3 --connectiontimeout=5

```
but my issue was getting it to work in conky. My problem was that I didn't have a "$" at the beginning of the line in .conkyrc.
I don't *think* the $ in your password should matter, but try escaping it like so:
```
password=randompa\$\$word
```
(as opposed to
```
password=randompa$$word
```)

But I'm pretty sure that's unnecessary.

---

### Post by .salo on 2009-06-14
this helps. Thanks.

---

### Post by kaivalagi on 2009-06-27
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

[LIST]
[*]Updated to expand ~ based template paths
[*]Updated to make safe the output to stop unwanted conky execution
[/LIST]

Changes can be found here: [https://launchpad.net/~m-buck/+archive/conky/+files/conkyemail_2.07_source.changes](https://launchpad.net/~m-buck/+archive/conky/+files/conkyemail_2.07_source.changes)

The first post is updated and the apt package should be available soon...

---

### Post by Da_Coynul on 2009-06-27
I am having a problem checking AOL mail.  It only happens when there are **zero** new messages, otherwise it works fine.  Here's the error:

> 
ERROR: getIMAPEmailData:Unexpected error:Traceback (most recent call last):
  File "conkyEmail.py", line 427, in getIMAPEmailData
    nums = data[0].split()
AttributeError: 'NoneType' object has no attribute 'split'

---

### Post by kaivalagi on 2009-06-28
> **Da_Coynul said:**
> I am having a problem checking AOL mail.  It only happens when there are **zero** new messages, otherwise it works fine.  Here's the error:

I wish you would have said something before I released the latest script :)

Give the attached .deb a try, it **_should_** have the issue fixed in it. I'll roll out a new version via apt when more changes have been made first

---

### Post by Da_Coynul on 2009-06-28
Tried it, but I'm still getting the same error :confused:

> **kaivalagi said:**
> I wish you would have said something before I released the latest script :)

Give the attached .deb a try, it **_should_** have the issue fixed in it. I'll roll out a new version via apt when more changes have been made first

---

### Post by Da_Coynul on 2009-06-28
Changing:

```

if data != None and len(data) > 0:
```

to
```

if data[0] != None and len(data) > 0:
```

Fixes AOL mail but breaks Gmail.  Could one of them be providing a non-standard response to imap.search?

Any thoughts?

> **Da_Coynul said:**
> Tried it, but I'm still getting the same error :confused:

---

### Post by n0_mad on 2009-06-28
I have problem with ConkyEmail and gmail. Sometimes Conky hangs in pipe_wait state and not updating anything, seems it waiting for ConkyEmail, wich hangs in do_wait state. If i remove  ConkyEmail from .conkyrc all works fine and no hangs. I think this happens when torrent client downloadig something. Is there any way i could fix this?

---

### Post by Ubentoo on 2009-08-19
[LEFT]Is there anyway I can define a global offset for the script? I'd like to have every line of the output 50 pixel (or 100 spaces etc)  away from the left border...

PS:
Looking through the code (getOutputData is probably relevant if not conky itself can do it) I found the following in line 555 in conkyEmail.py
```
# create new global **weather** object
```(Version from 27/06/2009) :)

-edit-
I experimented a little bit with rjust(n). Now I have to find out how this works as arguement, doesn't look to difficult, but it's too late for today...
[/LEFT]

---

### Post by Ubentoo on 2009-08-19
Hm, couldn't stop ... ;-)
If somebody is interested, here is the diff file, also with the slight modification that I removed the number of new emails (I prefer setting mailinfo high enough). rjust() does add spaces, but you have to use len (I just found ljust in getWrappedText and thought I could use it...), the far more straight forward way was a concatenation...
This will probably give bad results in combination with maxwidth and linelimit, but for me it's ok.

```

70,72d69
<     #
<     self.parser.add_option("--indent", dest="indent", default=0, type="int", metavar="NUMBER", help=u"[default: %default] The number of spaces for intendation")
<     #
147,149c144
<         #
<                 output = " "*self.options.indent + "No new Emails."#"0"
<         #
---
>                 output = "0"
154,156c149
<             #
<                     #output = "%s New"%count
<             #
---
>                     output = "%s New"%count
163,172c156,160
<                 #
<                             #bullet = "%s. "%(counter)
<                 
<                             text = "On %s from %s: %s%s%s"%(emaildata.recvdate,emaildata.sender,self.options.quote,emaildata.subject,self.options.quote)
<                             #text = bullet + self.getWrappedText(text, self.options.maxwidth, len(bullet), self.options.linelimit)
<                             text = " "*self.options.indent + text
<                   output = output + text
<                             if len(self.emaillist) >= counter + 1:
<                   output = output + "\n"
<                 #
---
>                             bullet = "%s. "%(counter)
> 
>                             text = "%s: %s%s%s"%(emaildata.sender,self.options.quote,emaildata.subject,self.options.quote)
>                             text = bullet + self.getWrappedText(text, self.options.maxwidth, len(bullet), self.options.linelimit)
>                             output = output + "\n" + text
562,564d549
<         # 
<         print >> sys.stdout, "    indent:",options.indent
<         #

```

---

### Post by mbux on 2009-08-23
Is it supposed to refresh when new mail arrives after you have started conky? Right not my conky will tell me what new mail I have when it first starts, but it won't let me know if new mail comes while it is running.

---

### Post by Ubentoo on 2009-08-25
Maybe the update interval is set to high? Mine is set to 60 seconds:  execi 60 conkyEmail

---

### Post by puma303 on 2009-08-30
i've got a very little problem : every time i recive an email or the counter must change (from 0 to 1 or from X to 0 after that i read the email) my conky go down the wallpaper, i mean : i can't see the conky i must kill him and run agan from terminal. Any help?

---

### Post by dreamer485 on 2009-10-11
Hi,
I have some kind of problem with my conkyEmail. When I point the script to any of my pop3 accounts the total number of messages is displayed (seen + unseen). I would like the script to print something like this: NewMessages/TotalMessages. Maybe I have to add some argument in the ${execi ...} command, but I don't know any. Will anybody please help me???
Thank you!!

---

### Post by kaivalagi on 2009-10-12
> **puma303 said:**
> i've got a very little problem : every time i recive an email or the counter must change (from 0 to 1 or from X to 0 after that i read the email) my conky go down the wallpaper, i mean : i can't see the conky i must kill him and run agan from terminal. Any help?

This will be due to your conky setup not the script, please post your conkyrc and the question on the main conkyrc thread for help
Thanks

---

### Post by kaivalagi on 2009-10-12
> **dreamer485 said:**
> Hi,
I have some kind of problem with my conkyEmail. When I point the script to any of my pop3 accounts the total number of messages is displayed (seen + unseen). I would like the script to print something like this: NewMessages/TotalMessages. Maybe I have to add some argument in the ${execi ...} command, but I don't know any. Will anybody please help me???
Thank you!!

For pop3 emails the count is purely on the number of emails, pop3 is crap and as such doesn't support new mail counts. New mail counts would have to be done in the script by keeping a log of all emails etc...if you want a decent mail count function switch to using IMAP based mail instead - if you have that feature available.

---

### Post by pisionik on 2009-10-15
```
${voffset -8}${font PizzaDude Bullets:size=14}B${font}  Mail: ${alignr}${font DejaVu Sans:style=Bold:size=8} ${execi 1800 conkyEmail --servertype=IMAP --servername=imap.gmail.com --username=teodor.cartman --password=***  --ssl}${font} New email(s)
```> psionik@HarryPotter:~$ conky
Conky: desktop window (14000a7) is subwindow of root window (83)
Conky: window type - normal
Conky: drawing to created window (0x4200001)
Conky: drawing to double buffer
ERROR: getIMAPEmailData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 396, in getIMAPEmailData
    imap.login(username, password)
  File "/usr/lib/python2.6/imaplib.py", line 501, in login
    raise self.error(dat[-1])
error: [ALERT] Web login required (Failure)


i have bad english, please tell me, where i do mistakes

---

### Post by kaivalagi on 2009-10-15
> **pisionik said:**
> ```
${voffset -8}${font PizzaDude Bullets:size=14}B${font}  Mail: ${alignr}${font DejaVu Sans:style=Bold:size=8} ${execi 1800 conkyEmail --servertype=IMAP --servername=imap.gmail.com --username=teodor.cartman --password=***  --ssl}${font} New email(s)
```

i have bad english, please tell me, where i do mistakes

Try using your full gmail address for the username, I think you'll need the @gmail.com or @googlemail.com suffix too...

Also, you need to ensure that your gmail account is setup to support IMAP, for this you need to go into the settings at the gmail website, see the attached screenshot of my account settings.

Hope that helps

---

### Post by pisionik on 2009-10-15
> **kaivalagi said:**
> Try using your full gmail address for the username, I think you'll need the @gmail.com or @googlemail.com suffix too...

Also, you need to ensure that your gmail account is setup to support IMAP, for this you need to go into the settings at the gmail website, see the attached screenshot of my account settings.

Hope that helps

i trying @gmail.com and @googlemail.com and my first step was setup to support IMAP on website)
but it's not help((
may be becouse logginname have "." - dot?

---

### Post by kaivalagi on 2009-10-15
> **pisionik said:**
> i trying @gmail.com and @googlemail.com and my first step was setup to support IMAP on website)
but it's not help((
may be becouse logginname have "." - dot?

I doubt the dot causes any issues, there is a dot in the domain name

Working for me as below:

```
conkyEmail --servertype=IMAP --servername=imap.googlemail.com --ssl --username=***@googlemail.com --password=*** --mailinfo=3
```

---

### Post by pisionik on 2009-10-15
> **kaivalagi said:**
> I doubt the dot causes any issues, there is a dot in the domain name

Working for me as below:

```
conkyEmail --servertype=IMAP --servername=imap.googlemail.com --ssl --username=***@googlemail.com --password=*** --mailinfo=3
```
hmm.. can u attach your /usr/share/conkyemail/conkyEmail.py 
                              and /usr/lib/python2.6/imaplib.py

---

### Post by kaivalagi on 2009-10-15
> **pisionik said:**
> hmm.. can u attach your /usr/share/conkyemail/conkyEmail.py 
                              and /usr/lib/python2.6/imaplib.py

I am using the code associated with the ppa packages

I assume you installed from the ppa too?

You can view all my ppa based deb packages and tarballs in launchpad here: [https://launchpad.net/~m-buck/+archive/conky/+packages](https://launchpad.net/~m-buck/+archive/conky/+packages)

The source for conkyEmail is here: [http://bazaar.launchpad.net/~m-buck/+junk/conkyemail/files](http://bazaar.launchpad.net/~m-buck/+junk/conkyemail/files)

Cheers

---

### Post by pisionik on 2009-10-15
> **kaivalagi said:**
> I am using the code associated with the ppa packages

I assume you installed from the ppa too?

You can view all my ppa based deb packages and tarballs in launchpad here: [https://launchpad.net/~m-buck/+archive/conky/+packages]("https://launchpad.net/%7Em-buck/+archive/conky/+packages")

The source for conkyEmail is here: [http://bazaar.launchpad.net/~m-buck/+junk/conkyemail/files]("http://bazaar.launchpad.net/%7Em-buck/+junk/conkyemail/files")

Cheers
and what?... i already setup this
what packages i need?
did you scared? attach your files.. with my doesn't work

---

### Post by kaivalagi on 2009-10-15
> **pisionik said:**
> and what?... i already setup this
what packages i need?
did you scared? attach your files.. with my doesn't work

The point is that my .py is the same as in the package (it was installed via method 1 in the first post)

If you have already followed the first post's method 1 then you will have what I have and all should work just fine. Any package dependancies are installed by default via apt-get/synaptic, but I think the imap library is part of the standard python install anyway (no extra python packages for it)

---

### Post by pisionik on 2009-10-17
can you make run string, when mouse on here?
sorry for my english

---

### Post by pisionik on 2009-10-17
> **kaivalagi said:**
> kaivalagi
can you make run string, when mouse on here?
sorry for my english

---

### Post by kaivalagi on 2009-10-17
> **pisionik said:**
> can you make run string, when mouse on here?
sorry for my english

I really don't understand what you mean :confused:

Have you tried using google translate to provide english text?	
&#1042;&#1099; &#1087;&#1099;&#1090;&#1072;&#1083;&#1080;&#1089;&#1100; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1100; Google, &#1095;&#1090;&#1086;&#1073;&#1099; &#1086;&#1073;&#1077;&#1089;&#1087;&#1077;&#1095;&#1080;&#1090;&#1100; &#1087;&#1077;&#1088;&#1077;&#1074;&#1086;&#1076; &#1072;&#1085;&#1075;&#1083;&#1080;&#1081;&#1089;&#1082;&#1080;&#1081; &#1090;&#1077;&#1082;&#1089;&#1090;?

---

### Post by yk1000 on 2009-10-24
Hi Kaivalagi,

Thank you for your wonderful script. I've been trying to use it on my gmail account using IMAP, which gives me the correct number of unread emails (when I do not use the mailinfo option). However, as soon as I put the mailinfo option, it gives me the following error:

conkyEmail --servertype=IMAP --servername=imap.gmail.com --username=%%% --password=%%% --ssl --verbose --mailinfo=2
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.gmail.com
    port: None
    folder: Inbox
    ssl: True
    username: %%%
    password: %%%
    template: None
    mailinfo: 2
    maxwidth: 80
    linelimit: 0
    quote: "
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Logging on to IMAP server: imap.gmail.com
INFO: Searching for new mail on IMAP server "imap.gmail.com" in folder "Inbox"
INFO: Extracting message data for IMAP server: imap.gmail.com
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
^CTraceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 560, in <module>
    main()
  File "/usr/share/conkyemail/conkyEmail.py", line 557, in main
    emailinfo.writeOutput()
  File "/usr/share/conkyemail/conkyEmail.py", line 472, in writeOutput
    output = self.getOutputData(self.options.servertype,self.options.servername,self.options.port,self.options.folder,self.options.ssl,self.options.username,self.options.password,self.options.connectiontimeout,self.options.mailinfo)
  File "/usr/share/conkyemail/conkyEmail.py", line 136, in getOutputData
    count = self.getIMAPEmailData(servername,port,folder,ssl,username,password,mailinfo)
  File "/usr/share/conkyemail/conkyEmail.py", line 439, in getIMAPEmailData
    typ, message = imap.fetch(num, '(BODY.PEEK[HEADER])')
  File "/usr/lib/python2.6/imaplib.py", line 437, in fetch
    typ, dat = self._simple_command(name, message_set, message_parts)
  File "/usr/lib/python2.6/imaplib.py", line 1059, in _simple_command
    return self._command_complete(name, self._command(name, *args))
  File "/usr/lib/python2.6/imaplib.py", line 889, in _command_complete
    typ, data = self._get_tagged_response(tag)
  File "/usr/lib/python2.6/imaplib.py", line 990, in _get_tagged_response
    self._get_response()
  File "/usr/lib/python2.6/imaplib.py", line 907, in _get_response
    resp = self._get_line()
  File "/usr/lib/python2.6/imaplib.py", line 1000, in _get_line
    line = self.readline()
  File "/usr/lib/python2.6/imaplib.py", line 1170, in readline
    char = self.sslobj.read(1)
  File "/usr/lib/python2.6/ssl.py", line 136, in read
    return self._sslobj.read(len)
KeyboardInterrupt

----
In particular, I think this line:
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
might be the root of the issue.

Can you help me?

---

### Post by kaivalagi on 2009-10-24
> **yk1000 said:**
> Hi Kaivalagi,

Thank you for your wonderful script. I've been trying to use it on my gmail account using IMAP, which gives me the correct number of unread emails (when I do not use the mailinfo option). However, as soon as I put the mailinfo option, it gives me the following error:

conkyEmail --servertype=IMAP --servername=imap.gmail.com --username=%%% --password=%%% --ssl --verbose --mailinfo=2
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.gmail.com
    port: None
    folder: Inbox
    ssl: True
    username: %%%
    password: %%%
    template: None
    mailinfo: 2
    maxwidth: 80
    linelimit: 0
    quote: "
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Logging on to IMAP server: imap.gmail.com
INFO: Searching for new mail on IMAP server "imap.gmail.com" in folder "Inbox"
INFO: Extracting message data for IMAP server: imap.gmail.com
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
INFO: Processing email data to determine 'From', 'Subject' and 'Received Date'
^CTraceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 560, in <module>
    main()
  File "/usr/share/conkyemail/conkyEmail.py", line 557, in main
    emailinfo.writeOutput()
  File "/usr/share/conkyemail/conkyEmail.py", line 472, in writeOutput
    output = self.getOutputData(self.options.servertype,self.options.servername,self.options.port,self.options.folder,self.options.ssl,self.options.username,self.options.password,self.options.connectiontimeout,self.options.mailinfo)
  File "/usr/share/conkyemail/conkyEmail.py", line 136, in getOutputData
    count = self.getIMAPEmailData(servername,port,folder,ssl,username,password,mailinfo)
  File "/usr/share/conkyemail/conkyEmail.py", line 439, in getIMAPEmailData
    typ, message = imap.fetch(num, '(BODY.PEEK[HEADER])')
  File "/usr/lib/python2.6/imaplib.py", line 437, in fetch
    typ, dat = self._simple_command(name, message_set, message_parts)
  File "/usr/lib/python2.6/imaplib.py", line 1059, in _simple_command
    return self._command_complete(name, self._command(name, *args))
  File "/usr/lib/python2.6/imaplib.py", line 889, in _command_complete
    typ, data = self._get_tagged_response(tag)
  File "/usr/lib/python2.6/imaplib.py", line 990, in _get_tagged_response
    self._get_response()
  File "/usr/lib/python2.6/imaplib.py", line 907, in _get_response
    resp = self._get_line()
  File "/usr/lib/python2.6/imaplib.py", line 1000, in _get_line
    line = self.readline()
  File "/usr/lib/python2.6/imaplib.py", line 1170, in readline
    char = self.sslobj.read(1)
  File "/usr/lib/python2.6/ssl.py", line 136, in read
    return self._sslobj.read(len)
KeyboardInterrupt

----
In particular, I think this line:
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
might be the root of the issue.

Can you help me?

i thought I had covered off all date formats that should come through in the message data, I need to look into the script to see how to overcome this error...not today...

---

### Post by Bruce M. on 2009-10-28
[CENTER][COLOR="DarkRed"]***Murphy's Law***[/COLOR]
If it can be broken; Murphy will find the way![/CENTER]

OK, any help with this?  My "new" ISP, while faster and cheaper (now I know why) doesn't do email well. Changing the password from the ***"abc123"*** default for new users breaks it.  I know, we've been fighting with them for a week.  So I went looking for something online.  Tried Gmail, but when I found all my "local" folders being copied to their Internet server I pulled the plug, shut down my connection, changed some settings in T-bird so it wouldn't work, went in with FF and deleted everything; account included.

Next I tried (after looking at a lot) [GMX Mail]("http://gmx.com/") ([Review]("http://email.about.com/od/freeemailreviews/gr/gmx_mail.htm")) - Looked GREAT!  Just what I wanted - could NOT create a new account and Google told me of others with the same problem.

Back to looking and I found [Lavabit]("http://http://lavabit.com/index.html") ([Review]("http://email.about.com/od/freeemailreviews/gr/lavabit.htm")) - Their basic Account (Free) suits my needs perfectly.  I do not want my email on a web server somewhere (IMAP), POP3 is fine, download it & delete it from the server in one simple action. *Oh did I mention it's run on CentOS ??*

Now with conkyEmail, I'm getting an **"Oops!"** here. :(

```
${execi 600 conkyEmail --servername=lavabit.com --servertype=pop --ssl --port=995 --username=username --password=password}
```

```
0 bruloo@bruloo: ~
Wed Oct 28, 13:04 $ conky -c ~/Conky/c-172 &
Conky: desktop window (1200003) is subwindow of root window (1a7)
Conky: drawing to desktop window
Conky: drawing to double buffer
[1] 16867
0 bruloo@bruloo: ~
Wed Oct 28, 13:04 $ ERROR: getOutputData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 141, in getOutputData
    if count == -1:
UnboundLocalError: local variable 'count' referenced before assignment
```

Now before you say that needs to be: **--servername=*pop.*lavabit.com**

Here's the settings from their website:
> Settings
Webmail information. Webmail Address: 	[https://lavabit.com/webmail](https://lavabit.com/webmail)
Incoming mail Settings. Incoming Mail Server: 	**lavabit.com**
POP3 Port: 	110
POP3 over SSL Port: 	995
IMAP4 Port: 	143
IMAP4 over SSL Port: 	993
Outgoing mail Settings. Outgoing Mail Server: 	**lavabit.com**
SMTP Ports: 	25, 587, 2525, or 3535
SMTP over SSL Port: 	465

Any help for this old dude?

Have a nice day.
Bruce

---

### Post by kaivalagi on 2009-10-28
> **Bruce M. said:**
> [CENTER][COLOR="DarkRed"]***Murphy's Law***[/COLOR]
If it can be broken; Murphy will find the way![/CENTER]

OK, any help with this?  My "new" ISP, while faster and cheaper (now I know why) doesn't do email well. Changing the password from the ***"abc123"*** default for new users breaks it.  I know, we've been fighting with them for a week.  So I went looking for something online.  Tried Gmail, but when I found all my "local" folders being copied to their Internet server I pulled the plug, shut down my connection, changed some settings in T-bird so it wouldn't work, went in with FF and deleted everything; account included.

Next I tried (after looking at a lot) [GMX Mail]("http://gmx.com/") ([Review]("http://email.about.com/od/freeemailreviews/gr/gmx_mail.htm")) - Looked GREAT!  Just what I wanted - could NOT create a new account and Google told me of others with the same problem.

Back to looking and I found [Lavabit]("http://http://lavabit.com/index.html") ([Review]("http://email.about.com/od/freeemailreviews/gr/lavabit.htm")) - Their basic Account (Free) suits my needs perfectly.  I do not want my email on a web server somewhere (IMAP), POP3 is fine, download it & delete it from the server in one simple action. *Oh did I mention it's run on CentOS ??*

Now with conkyEmail, I'm getting an **"Oops!"** here. :(

```
${execi 600 conkyEmail --servername=lavabit.com --servertype=pop --ssl --port=995 --username=username --password=password}
```

```
0 bruloo@bruloo: ~
Wed Oct 28, 13:04 $ conky -c ~/Conky/c-172 &
Conky: desktop window (1200003) is subwindow of root window (1a7)
Conky: drawing to desktop window
Conky: drawing to double buffer
[1] 16867
0 bruloo@bruloo: ~
Wed Oct 28, 13:04 $ ERROR: getOutputData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 141, in getOutputData
    if count == -1:
UnboundLocalError: local variable 'count' referenced before assignment
```

Now before you say that needs to be: **--servername=*pop.*lavabit.com**

Here's the settings from their website:


Any help for this old dude?

Have a nice day.
Bruce

Looks like you found a bug with the script...might be able to fix it at the weekend

---

### Post by Bruce M. on 2009-10-28
> **kaivalagi said:**
> Looks liek you foudn a bug with the script...might be able to fix it at the weekend

No such thing as a bug in a K app, undocumented feature maybe, but no bugs.

C H I M O!
Bruce

---

### Post by kaivalagi on 2009-11-01
[COLOR=Red]I have switched OS and now use **ArchLinux** rather than any debian based distro. It looks like the continuing support of my scripts will be **without ppa updates**, and instead my time will support AUR based installs once I get to understand them. I will provide the usual tarball downloads of the source for non Arch users from within these forum.[/COLOR]

---

### Post by plytheman on 2009-11-18
Hey kaivalagi, wanted to thank you for the awesome script, got conky monitoring my university mail now!  Step by step im making myself nice and at home in crunchbang.

My question is (maybe) less about the conkyEmail script itself and purely sylistic.  I found a dingbat font with an envelope I liked and placed it after the number of new mail, is there any way to switch the font color to red if I have new mail and keep it grey (default) when the number is 0?

Obviously it's nothing important so if it can't be done or isn't worth the effort I understand.  I don't really know much about programming myself and can't think of a way of making $if_existing work with that.

---

### Post by kaivalagi on 2009-11-18
> **plytheman said:**
> Hey kaivalagi, wanted to thank you for the awesome script, got conky monitoring my university mail now!  Step by step im making myself nice and at home in crunchbang.

My question is (maybe) less about the conkyEmail script itself and purely sylistic.  I found a dingbat font with an envelope I liked and placed it after the number of new mail, is there any way to switch the font color to red if I have new mail and keep it grey (default) when the number is 0?

Obviously it's nothing important so if it can't be done or isn't worth the effort I understand.  I don't really know much about programming myself and can't think of a way of making $if_existing work with that.

I think the guys over at the conkyrc and conky hardcore have done a similar thing with sensor output for temp, maybe that with shed some clues on how to achieve what you want. You will require a shell script which conky calls which in turn calls this script I think.

---

### Post by plytheman on 2009-11-18
Thanks for the lead on conky hardcore.  I checked through the write up on the basics of $if_existing and couldn't figure it out but sure enough in the next menu item down past 'Tips and Tricks' there's a colorize script!  [Here](http://conky.linux-hardcore.com/?page_id=747) is the link for anyone else that wants to play with it.  

Stuck at school now but this will be top priority to get running when I get home, hopefully I can post back with some good results.  (Screw studying for organic chem, I'm making that envelope red!)

---

### Post by kaivalagi on 2009-11-18
> **plytheman said:**
> Screw studying for organic chem, I'm making that envelope red!

I'm looking forward to seeing what script you come up with :)

---

### Post by Bruce M. on 2009-11-18
hey K - have you have a chance to look at [Murphy's Law]("http://ubuntuforums.org/showpost.php?p=8181352&postcount=289") yet?

Wife is wondering why it always says "0" emails.  :)

CHIMO!
Bruce

---

### Post by kaivalagi on 2009-11-19
> **Bruce M. said:**
> Now with conkyEmail, I'm getting an **"Oops!"** here. :(

```
${execi 600 conkyEmail --servername=lavabit.com --servertype=pop --ssl --port=995 --username=username --password=password}
```

```
0 bruloo@bruloo: ~
Wed Oct 28, 13:04 $ conky -c ~/Conky/c-172 &
Conky: desktop window (1200003) is subwindow of root window (1a7)
Conky: drawing to desktop window
Conky: drawing to double buffer
[1] 16867
0 bruloo@bruloo: ~
Wed Oct 28, 13:04 $ ERROR: getOutputData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 141, in getOutputData
    if count == -1:
UnboundLocalError: local variable 'count' referenced before assignment
```


> **Bruce M. said:**
> hey K - have you have a chance to look at [Murphy's Law]("http://ubuntuforums.org/showpost.php?p=8181352&postcount=289") yet?

Wife is wondering why it always says "0" emails.  :)

CHIMO!
Bruce

Sorry, totally forgot about that problem post, too much on...and Arch to play with :)

I have looked at the code and I can see how this issue might occur, I think your option of "--servertype=**[COLOR="Red"]pop[/COLOR]**" needs to become "--servertype=**[COLOR="Green"]POP[/COLOR]**". Don't you know all things linux are case sensitive :)

Although that is no excuse, I really need to make the script more flexible so it can take either case!...not right now though ;)

---

### Post by Bruce M. on 2009-11-19
> **kaivalagi said:**
> Sorry, totally forgot about that problem post, too much on...and Arch to play with :)

I have looked at the code and I can see how this issue might occur, I think your option of "--servertype=**[COLOR="Red"]pop[/COLOR]**" needs to become "--servertype=**[COLOR="Green"]POP[/COLOR]**". Don't you know all things linux are case sensitive :)

Although that is no excuse, I really need to make the script more flexible so it can take either case!...not right now though ;)

Oh for cryin' out loud! That is just so silly of me.
I've only written a few hundred conky files, you'd think I know.

That's a "DUH!" if I ever heard one.  :)

Colour me: **[COLOR="Red"]Embarrassed[/COLOR]**

So how's ARCH?  I'm a #!'er it now.  :)  [Love Open Box!!]("http://conky.linux-hardcore.com/?page_id=3651") (check bottom of page)

CHIMO Mate!
And a HUGE Thanks. (it's working)
Bruce

---

### Post by Wim De Winter on 2009-11-20
works like a dream!! Thanks a lot!!

---

### Post by dilch on 2009-11-20
hi, first thx for the great conkytool.
i've got just one question.


this is one of my conkyliness
```
${font DejaVu Sans:size=6}${execi 1800 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --port=993 --username=secret@googlemail.com --password="don't tell ya" --mailinfo=2 --ssl}${goto 1000}}${rss http://www.werder.de/aktuelles/rss/index.xml 10 item_titles 3}${font}
```

so, the emailprog is using 3 lines,
2 new
first new email
second new email

and the rss-feed also uses 3 lines.
the emailview is on my left, rss on my right desktopside. i've got a problem because the rss-feed is now "under" my emailine, so it looks like i have aempty lines on the right. any solution?

perhaps there is an easy positioncommandslution but i am realy to stupid to understand it

---

### Post by kaivalagi on 2009-11-21
> **dilch said:**
> hi, first thx for the great conkytool.
i've got just one question.


this is one of my conkyliness
```
${font DejaVu Sans:size=6}${execi 1800 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --port=993 --username=secret@googlemail.com --password="don't tell ya" --mailinfo=2 --ssl}${goto 1000}}${rss http://www.werder.de/aktuelles/rss/index.xml 10 item_titles 3}${font}
```

so, the emailprog is using 3 lines,
2 new
first new email
second new email

and the rss-feed also uses 3 lines.
the emailview is on my left, rss on my right desktopside. i've got a problem because the rss-feed is now "under" my emailine, so it looks like i have aempty lines on the right. any solution?

perhaps there is an easy positioncommandslution but i am realy to stupid to understand it

The easiest option is to run 2 conkies and position the conky windows next to each other, 1 for email info and the other for rss feed data, that way each has it's own "space" no matter how much content is output for either.

---

### Post by snkiz on 2009-12-29
hi ya K, hope arch is being nice to you. I ran into a small issue today. It seems either my isp or google is having long ping times today, consequently conkyemail is timing out. This  unfortunately taking the conky window its housed in with it. (Bad cuz my clock is there.) Heres my xsession log entry:
```
ERROR: Server connection error: HTTP Error 503: Service Unavailable
ERROR: Server connection error: HTTP Error 503: Service Temporarily Unavailable
ERROR: Server connection error: <urlopen error timed out>
/home/snkiz/bin/conkynow: line 36:  2567 Segmentation fault      conky -c mainrc
``` 
If there is a bulitin way to fix it I'm sorry I missed it. If this has been brought up before, again sorry, its a long thread now. Anyways keep up the great work, and thanks again. Cheers!

---

### Post by kaivalagi on 2009-12-30
> **snkiz said:**
> hi ya K, hope arch is being nice to you. I ran into a small issue today. It seems either my isp or google is having long ping times today, consequently conkyemail is timing out. This  unfortunately taking the conky window its housed in with it. (Bad cuz my clock is there.) Heres my xsession log entry:
```
ERROR: Server connection error: HTTP Error 503: Service Unavailable
ERROR: Server connection error: HTTP Error 503: Service Temporarily Unavailable
ERROR: Server connection error: <urlopen error timed out>
/home/snkiz/bin/conkynow: line 36:  2567 Segmentation fault      conky -c mainrc
``` 
If there is a bulitin way to fix it I'm sorry I missed it. If this has been brought up before, again sorry, its a long thread now. Anyways keep up the great work, and thanks again. Cheers!

You could try extending the connection timeout of the script:

```
-c NUMBER, --connectiontimeout=NUMBER
                        [default: 10] Define the number of seconds before a
                        connection timeout can occur. Not applicable at
                        command line when using templates.


```

The other option is that you run the script via a cron job outputting to a text file, and then load the text via the cat command...just a means to disconnect conky directly with the script and allow it to start promptly...

---

### Post by kaivalagi on 2010-01-09
[SIZE="1"][COLOR="RoyalBlue"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: [http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)[/COLOR][/SIZE]

**[COLOR="Blue"][SIZE="3"]IMPORTANT NEWS[/SIZE]**

All the script packages have now been copied into the Conky Hardcore PPA. Any package updates will be provided by the team through this new ppa.

The ppa can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/~conkyhardcore/+archive/ppa")

To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck*
```
Then follow the modified first post instructions for the scripts
[/COLOR]

---

### Post by rajadain on 2010-02-22
Hi,
 I use the script to access my live mail account. I use it as follows:
[HTML]conkyEmail --servertype=POP --servername=pop3.live.com --port=995 --ssl --username=myname@live.com --password=mypass
[/HTML]
 Instead of getting new messages, it returns ALL the messages in the inbox. Now, if Live Mail had a feature like All Mail or Archive like GMail, I suppose I could've redirected stuff into that from time to time. But as it doesn't, I really need it to detect the number of new messages. I'll be happy if it can just detect whether or not there are unread messages.
 Also, when using this with my GMail, I use it as follows:
[HTML]conkyEmail --servertype=IMAP --servername=imap.gmail.com --port=993 --ssl --username=myname@gmail.com --password=mypass
[/HTML]
 When there are only a couple of unread messages, it works fine. But when there were 4 unread messages, it returned 8. Other scripts which use the GMail atom feed returned the correct number, as did my GMail Notifier Google Chrome plugin. I hope this can be fixed!
 But I have another script which uses the GMail Atom feed, so I can use that for GMail. But I really need a hotmail script, and I haven't been able to find another, and don't know enough scripting to write one on my own :(. And I have a ton of email accounts, all of whose notifications I get instantly in Windows Vista, but not in Ubuntu :(. This would really help.
 Thanks in advance for any assistance. :)

---

### Post by kaivalagi on 2010-02-23
> **rajadain said:**
> Hi,
 I use the script to access my live mail account. I use it as follows:
[HTML]conkyEmail --servertype=POP --servername=pop3.live.com --port=995 --ssl --username=myname@live.com --password=mypass
[/HTML]
 Instead of getting new messages, it returns ALL the messages in the inbox. Now, if Live Mail had a feature like All Mail or Archive like GMail, I suppose I could've redirected stuff into that from time to time. But as it doesn't, I really need it to detect the number of new messages. I'll be happy if it can just detect whether or not there are unread messages.
 Also, when using this with my GMail, I use it as follows:
[HTML]conkyEmail --servertype=IMAP --servername=imap.gmail.com --port=993 --ssl --username=myname@gmail.com --password=mypass
[/HTML]
 When there are only a couple of unread messages, it works fine. But when there were 4 unread messages, it returned 8. Other scripts which use the GMail atom feed returned the correct number, as did my GMail Notifier Google Chrome plugin. I hope this can be fixed!
 But I have another script which uses the GMail Atom feed, so I can use that for GMail. But I really need a hotmail script, and I haven't been able to find another, and don't know enough scripting to write one on my own :(. And I have a ton of email accounts, all of whose notifications I get instantly in Windows Vista, but not in Ubuntu :(. This would really help.
 Thanks in advance for any assistance. :)

I can't do anything about your POP mail notification showing only new mails, without storing the emails locally which they are not. The only way that this script can work as you want, without lots of time spent on it, is if you retrieve your email messages with a mail client which has been setup to not leave the messages on the server. Personally I think POP is a very poorly spec'ed email protocol and should be phased out, IMAP is soooo much better.

I have never had double the messages returned via IMAP (Gmail or otherwise). If you set --mailinfo to say 10 do you see the same message subjects doubled up too?

**[COLOR="Navy"]Edit: what you could be seeing with gmail is multiple emails with the same person listed out separately as would be done in any IMAP client, in gmail they are combined together to show as one item in the list[/COLOR]**

---

### Post by rajadain on 2010-02-25
> **kaivalagi said:**
> Personally I think POP is a very poorly spec'ed email protocol and should be phased out, IMAP is soooo much better.

**[COLOR="Navy"]Edit: what you could be seeing with gmail is multiple emails with the same person listed out separately as would be done in any IMAP client, in gmail they are combined together to show as one item in the list[/COLOR]**

I actually searched the net after posting this, and Live Mail not supporting IMAP has made a lot of people upset, including me now :(. I guess I'll just have to live with it until something happens (and with Microsoft that's always an overoptimistic thought).

I agree that when you have fast unlimited internet and multiple access points (OSs or devices) then IMAP makes more sense. However, for those who do not have these features, POP still makes sense (like in India, where you have to pay for every MB). Also for people with limited email space, POP is better as it allows you to archive your copy on your disk while emptying the server. GMail makes this redundant, but lets not let modern convenience disable us from thinking about real hardship. I also don't like how my mail client hangs for a while when contacting the IMAP server. This happens both on Windows Live Mail on Vista and Evolution Mail in Ubuntu. I think that IMAP could still use work.

---

### Post by kaivalagi on 2010-02-25
> **rajadain said:**
> I actually searched the net after posting this, and Live Mail not supporting IMAP has made a lot of people upset, including me now :(. I guess I'll just have to live with it until something happens (and with Microsoft that's always an overoptimistic thought).

I agree that when you have fast unlimited internet and multiple access points (OSs or devices) then IMAP makes more sense. However, for those who do not have these features, POP still makes sense (like in India, where you have to pay for every MB). Also for people with limited email space, POP is better as it allows you to archive your copy on your disk while emptying the server. GMail makes this redundant, but lets not let modern convenience disable us from thinking about real hardship. I also don't like how my mail client hangs for a while when contacting the IMAP server. This happens both on Windows Live Mail on Vista and Evolution Mail in Ubuntu. I think that IMAP could still use work.

I remember the days of pay per minute for internet, painful...still I wouldn't have thought that you'll be in the position of paying per MB for much longer, you'll just have a low cap on monthly totals next when the Indian telcos move into this century. I assume you are living in a more rural area of India where the tech available is limited?

---

### Post by rajadain on 2010-02-26
> **kaivalagi said:**
> I remember the days of pay per minute for internet, painful...still I wouldn't have thought that you'll be in the position of paying per MB for much longer, you'll just have a low cap on monthly totals next when the Indian telcos move into this century. I assume you are living in a more rural area of India where the tech available is limited?

Well, now I'm in the US with unlimited high-speed internet :D. But I just moved 6 months ago, so I'm well in touch with the modern day facilities available. Better things are happening, but the sheer magnitude of demand and still lacking infrastructure makes the process slow. A speed of 2 Mbit/s is considered "very good", and usually comes with a cap of 1 / 2.5 / 4 / 8 / 12 GB per month based on what you pay, and if you cross that limit you pay per MB. The average Joe can afford the 2.5 GB / month plan, and that really suffices unless you watch a lot of videos. Some come with a night-unlimited period (usually from 2 - 8 AM) in which transfer doesn't count. Most all-day unlimited plans sport considerably lower speeds, ~ 256 kbps. And this isn't rural India, this is in the second-tier cities (those that come after Delhi, Mumbai, Chennai, Bangalore, Kolkata and Ahmedabad). And the speeds in the first tier cities aren't much better either.

But India has a very good cellular infrastructure. People in general use cellphones much more than computers. Illiteracy might have something to do with that.

It's a very interesting country with very interesting people and very interesting problems. You should visit sometime. It promises to leave an indelible impression. :)

---

### Post by kaivalagi on 2010-02-27
> **rajadain said:**
> It's a very interesting country with very interesting people and very interesting problems. You should visit sometime. It promises to leave an indelible impression. :)

Maybe I'll visit one day, I've always wanted to go to Kerala down south for the Onam festival when it's on.

I have interests elsewhere though, I met my wife in Fiji and lived and worked there for over 3 years. There is plenty of Indian culture in Fiji too, somewhere between 1/3 to 1/2 Hindu population. But the south pacific lifestyle is what does it for me, whether you're Indian, English or Fijian the warmth people share in the south pacific makes up for any missed luxuries :)

---

### Post by alecive on 2010-03-19
Hi!

I'm trying conkyemail, and it's a very very useful script!! :D

But I have a problem: I tried to use this script with an account on gmx.com (and setting --servertype=IMAP).

If I try to view other folders than Inbox (like Spam, Drafts, etc) all go right, but if I try to view the folders relatives to my Mail Collector (i.e. the inbox folder of other mails) the script give me this error:

```
ERROR: getIMAPEmailData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 421, in getIMAPEmailData
    typ, data = imap.search(None, self.IMAP_SEARCH_OPTION)
  File "/usr/lib/python2.6/imaplib.py", line 620, in search
    typ, dat = self._simple_command(name, *criteria)
  File "/usr/lib/python2.6/imaplib.py", line 1058, in _simple_command
    return self._command_complete(name, self._command(name, *args))
  File "/usr/lib/python2.6/imaplib.py", line 818, in _command
    ', '.join(Commands[name])))
error: command SEARCH illegal in state AUTH, only allowed in states SELECTED

```

How can I get rid of this?

Thanks for the response!! :D

---

### Post by kaivalagi on 2010-03-19
> **alecive said:**
> Hi!

I'm trying conkyemail, and it's a very very useful script!! :D

But I have a problem: I tried to use this script with an account on gmx.com (and setting --servertype=IMAP).

If I try to view other folders than Inbox (like Spam, Drafts, etc) all go right, but if I try to view the folders relatives to my Mail Collector (i.e. the inbox folder of other mails) the script give me this error:

```
ERROR: getIMAPEmailData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 421, in getIMAPEmailData
    typ, data = imap.search(None, self.IMAP_SEARCH_OPTION)
  File "/usr/lib/python2.6/imaplib.py", line 620, in search
    typ, dat = self._simple_command(name, *criteria)
  File "/usr/lib/python2.6/imaplib.py", line 1058, in _simple_command
    return self._command_complete(name, self._command(name, *args))
  File "/usr/lib/python2.6/imaplib.py", line 818, in _command
    ', '.join(Commands[name])))
error: command SEARCH illegal in state AUTH, only allowed in states SELECTED

```

How can I get rid of this?

Thanks for the response!! :D

Absolutely no idea at all, I don't a mail setup anything like what you are talking about. It looks like the "other"mailboxes are not implemented in true IMAP fashion???

---

### Post by alecive on 2010-03-20
> **kaivalagi said:**
> Absolutely no idea at all, I don't a mail setup anything like what you are talking about. It looks like the "other"mailboxes are not implemented in true IMAP fashion???

I don't know if it's a problem of the IMAP protocol or of the script.. but it seemed to me that in Thunderbird I had the possibility to see also other mailboxes..However, currently I haven't the possibility to verify this, because I use only webmail..

The problem is that I have an account on gmx.com, and through this I can see the Inbox of others two mail accounts (gmail.com and toshiba-connect.it); a workaround could be using conkyEmail for these three accounts distincly. But the problem is that I don't remember the POP3 server of the second mail account!! And the support mail of this email account no longer exist!

:(

---

### Post by kaivalagi on 2010-03-20
> **alecive said:**
> I don't know if it's a problem of the IMAP protocol or of the script.. but it seemed to me that in Thunderbird I had the possibility to see also other mailboxes..However, currently I haven't the possibility to verify this, because I use only webmail..

The problem is that I have an account on gmx.com, and through this I can see the Inbox of others two mail accounts (gmail.com and toshiba-connect.it); a workaround could be using conkyEmail for these three accounts distincly. But the problem is that I don't remember the POP3 server of the second mail account!! And the support mail of this email account no longer exist!

:(

Can you take a screenshot or something of the multiple mailboxes (need to see the folder names etc) and post it? Obscure the email addresses them selves if they are visible...

Can't promise anything...but having a better understanding may help

---

### Post by alecive on 2010-03-20
> **kaivalagi said:**
> Can you take a screenshot or something of the multiple mailboxes (need to see the folder names etc) and post it? Obscure the email addresses them selves if they are visible...

Can't promise anything...but having a better understanding may help


Sure! Here you are the screenshot: is the left sidebar of my gmx account..
[[IMG]http://upload.centerzone.it/images/24507288877996973776_thumb.jpg[/IMG]](http://upload.centerzone.it/viewer.php?file=24507288877996973776.png)
What I cannot view are the folders in the mail collector..Sorry if my explaination is a bit difficult to understand, but I have only a basic knowledge of english!
I tried to add the option ***--folder=***@gmail.com ***but the result is what I posted yesterday.. :(

---

### Post by kaivalagi on 2010-03-20
> **alecive said:**
> Sure! Here you are the screenshot: is the left sidebar of my gmx account..
[[IMG]http://upload.centerzone.it/images/24507288877996973776_thumb.jpg[/IMG]](http://upload.centerzone.it/viewer.php?file=24507288877996973776.png)
What I cannot view are the folders in the mail collector..Sorry if my explaination is a bit difficult to understand, but I have only a basic knowledge of english!
I tried to add the option ***--folder=***@gmail.com ***but the result is what I posted yesterday.. :(

Any folders inside the Mail Collector folder which could represent the email accounts instead? I am wondering if the folder names you are using are not IMAP based...I get the feeling that the mail collector function is build out of proprietary technology and isn't IMAP compliant...

If I were you I would ask the support guys at gmx if using IMAP to get stuff out of the collector is possible

I don't think there is any more I can help you with on this, speak to gmx as it relates to their service not my script (I think)

---

### Post by e64462 on 2010-06-07
I've seen references to people successfully modifying conkyEmail.py to play a sound when new emails are detected. Does anyone have any experience or insight they can share?

---

### Post by kaivalagi on 2010-06-09
> **e64462 said:**
> I've seen references to people successfully modifying conkyEmail.py to play a sound when new emails are detected. Does anyone have any experience or insight they can share?

links? Yes in theory it would be possible if done via a shell script from conky...

---

### Post by e64462 on 2010-06-09
The link was on the archlinux forum, it was just a guy who said he had modified conkyEmail.py to do so. He didn't actually discuss what he had done at all, or what changes he had made. I was just hoping you had an idea or knew how it might be implemented. 

Thanks!
Nick

---

### Post by kaivalagi on 2010-06-10
> **e64462 said:**
> The link was on the archlinux forum, it was just a guy who said he had modified conkyEmail.py to do so. He didn't actually discuss what he had done at all, or what changes he had made. I was just hoping you had an idea or knew how it might be implemented. 

Thanks!
Nick

You can play sounds using "aplay" in the linux terminal, this could be used in by a shell script if mail was found using the script...

You would need something like this (probably wont work but should help you get there...I haven't tested it!). It gets output to a file and if more than one lines i.e. there are subject lines output for new mail then play a sound file.

```
#!/bin/sh
# get email output from script
conkyEmail [account options] > /tmp/emailout.txt
lines=`wc -l /tmp/emailout.txt | cut -c1-2`
# are there emails in the output
if test $lines -gt 1
then
 aplay [sound file]
fi
# output text for conky
cat /tmp/emailout.txt

```

If that was saved in a file /home/user/emailcheck.sh and made executable, you could then call this from conky in the rc file like this:

```
${execi 900 /home/user/emailcheck.sh}
```

Hope that helps

---

### Post by e64462 on 2010-06-11
It most certainly did, thank you!

I wasn't satisfied with the method of simply determining whether unread messages exist, because i use my inbox as a bit of a todo list; with emails sometimes sitting there for weeks at a time. So I didn't want it beeping at me every time it checked my inbox. But I modified it to audibly alert me only if there are more emails than the last time it checked. It's late, and I'm heading to bed but I'll try to post it when I wake up.

---

### Post by kaivalagi on 2010-06-11
Good job....I always like seeing some new creative stuff :)

---

### Post by e64462 on 2010-06-11
So thanks again for your suggestion, it set me on the right track. I don't really know why I didn't think to implement it that way... but here's what I did.

```
#!/bin/sh

TERM=vt100; export TERM

#get old email count from file
if [ ! -e /tmp/emailcount ]; then
	echo 0 > /tmp/emailcount
fi
oldCount=`cat /tmp/emailcount`

# get new email count from script
conkyEmail [OPTIONS] > /tmp/emailcount

# output text for conky
cat /tmp/emailcount

# play sound if new emails are detected
newCount=`cat /tmp/emailcount`
if [ $oldCount = "" ] && [ $newCount -gt 0 ]; then
	mplayer -really-quiet /path/file.wav &>/dev/null
else
	newMsgs=$(($newCount-$oldCount))
	if [ $newMsgs -gt 0 ]; then
		mplayer -really-quiet /path/file.wav &>/dev/null
	fi
fi
```

thanks again, works like a charm!

---

### Post by karthick87 on 2010-06-13
I have installed conkyemail and i have enabled[COLOR=Red] IMAP[/COLOR] in gmail..What next..?How to call this [COLOR=Red]conkyemail[/COLOR] in my conky script..?

---

### Post by kaivalagi on 2010-06-13
> **getyourkarthick said:**
> I have installed conkyemail and i have enabled[COLOR=Red] IMAP[/COLOR] in gmail..What next..?How to call this [COLOR=Red]conkyemail[/COLOR] in my conky script..?

There is an example conkyrc and template file in the /usr/share/conkyemail/example folder from the install, as mentioned in the first post. Should make sense when you look at them, once you create your own put them somewhere in your home folder and call conky giving it the rc file location like this:

```
conky -c /home/folder/conkyrcfile
```

You can always run the following to get pretty decent help on the scripts use:

```
conkyEmail -h
```

You can call conky lots of times for lots of files, search for "conkyrc" in this forum and you should find a lot of info on it's use :)

A good guide on conky can be found here: [http://conky.linux-hardcore.com/](http://conky.linux-hardcore.com/)

---

### Post by karthick87 on 2010-06-13
I am not familiar with conky,pls explain me a bit more..I need only GMAIL..

---

### Post by kaivalagi on 2010-06-13
Have a look at this: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

then read the first post and just try it, there are example files I have mentioned that you can copy. copy them somewhere and edit them to have your details in them, then run conky as I have mentioned before and see what happens.

---

### Post by karthick87 on 2010-06-15
Is it necessary to configure evolution..?

---

### Post by kaivalagi on 2010-06-15
> **getyourkarthick said:**
> Is it necessary to configure evolution..?
Evolution is a mail client, the script is a mail client of sorts too, so no

---

### Post by karthick87 on 2010-06-15
I have added this in my conkyrc file,but its not working...

${voffset 4}${font Liberation Sans:style=Bold:size=8}EMAIL $stippled_hr${font}
${execi 60 ~/.conkycolors/bin/conkyEmail --servertype=IMAP --servername=imap.gmail.com --username=XXXXXX --password=XXXXXXX}

---

### Post by karthick87 on 2010-06-16
I have added this in my conky script,

${voffset 4}${font Liberation Sans:style=Bold:size=8}EMAIL $stippled_hr${font}
${execi 1800 python ~/.Scripts/conkyEmail.py --servertype=IMAP --servername=imap.gmail.com --username=XXXXXX --password=XXXXXXXXX}

but i am unable to view the output.

---

### Post by kaivalagi on 2010-06-16
Try running the command part in the terminal like this first:

```
python /path/to/file/conkyEmail.py ...options... --verbose

```

With the verbose flag you'll have more to go on

The script works fine, it's been tried and tested over and over so it must be something you are doing wrong

Cheers

---

### Post by karthick87 on 2010-06-16
This is the terminal output,

```
karthick@Ubuntu-desktop:~$ python ~/.Scripts/conkyEmail.py --servertype=IMAP --servername=imap.gmail.com --username=XXXX --password=XXXX --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.gmail.com
    ssl: False
    username: XXXX
    password: XXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to IMAP server: imap.gmail.com
*** ERROR:getIMAPEmailData:Unexpected error:  <class 'socket.timeout'>
?

```

---

### Post by kaivalagi on 2010-06-17
> **getyourkarthick said:**
> This is the terminal output,

```
karthick@Ubuntu-desktop:~$ python ~/.Scripts/conkyEmail.py --servertype=IMAP --servername=imap.gmail.com --username=XXXX --password=XXXX --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.gmail.com
    ssl: False
    username: XXXX
    password: XXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to IMAP server: imap.gmail.com
*** ERROR:getIMAPEmailData:Unexpected error:  <class '[COLOR="Red"][SIZE="3"]socket.timeout[/SIZE][/COLOR]'>
?

```

The mail server is too slow to respond, use this option:

```
 -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10] Define the number of seconds before a
                        connection timeout can occur. Not applicable at
                        command line when using templates.

```

That should sort it out for you...the default connection timeout is only 10 seconds, I would try 30 then if no joy 60 seconds...

---

### Post by karthick87 on 2010-06-17
> **kaivalagi said:**
> The mail server is too slow to respond, use this option:

```
 -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10] Define the number of seconds before a
                        connection timeout can occur. Not applicable at
                        command line when using templates.

```That should sort it out for you...the default connection timeout is only 10 seconds, I would try 30 then if no joy 60 seconds...


Do you want me to add the above option??If so where to add the above script..?

---

### Post by kaivalagi on 2010-06-17
> **getyourkarthick said:**
> Do you want me to add the above option??If so where to add the above script..?

Come on your using linux, this is linux basics...the option can go anywhere in the list of options you provide e.g.

```
python ~/.Scripts/conkyEmail.py [COLOR="Red"]-c 30[/COLOR] --servertype=IMAP --servername=imap.gmail.com --username=XXXX --password=XXXX [COLOR="red"]--verbose[/COLOR]
```

But once working remember to lose the --verbose before using in conky

You should also be able to use the --ssl option with gmail too!

---

### Post by karthick87 on 2010-06-17
Still no use :(

```
karthick@Ubuntu-desktop:~$ python ~/.Scripts/conkyEmail.py -c 30 --servertype=IMAP --servername=imap.gmail.com --username=XXXX --password=XXXX --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.gmail.com
    ssl: False
    username: XXXX
    password: XXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to IMAP server: imap.gmail.com
*** ERROR:getIMAPEmailData:Unexpected error:  <class 'socket.error'>
?

```

Tried[COLOR=Red] -c 60[/COLOR]

```
karthick@Ubuntu-desktop:~$ python ~/.Scripts/conkyEmail.py -c 60 --servertype=IMAP --servername=imap.gmail.com --username=XXXX --password=XXXX --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.gmail.com
    ssl: False
    username: XXXX
    password: XXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to IMAP server: imap.gmail.com
*** ERROR:getIMAPEmailData:Unexpected error:  <class 'socket.error'>
?
```

---

### Post by kaivalagi on 2010-06-18
> **getyourkarthick said:**
> Still no use :(

```
karthick@Ubuntu-desktop:~$ python ~/.Scripts/conkyEmail.py -c 30 --servertype=IMAP --servername=imap.gmail.com --username=XXXX --password=XXXX --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.gmail.com
    ssl: False
    username: XXXX
    password: XXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to IMAP server: imap.gmail.com
*** ERROR:getIMAPEmailData:Unexpected error:  <class 'socket.error'>
?

```

Tried[COLOR=Red] -c 60[/COLOR]

```
karthick@Ubuntu-desktop:~$ python ~/.Scripts/conkyEmail.py -c 60 --servertype=IMAP --servername=imap.gmail.com --username=XXXX --password=XXXX --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.gmail.com
    ssl: False
    username: XXXX
    password: XXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to IMAP server: imap.gmail.com
*** ERROR:getIMAPEmailData:Unexpected error:  <class 'socket.error'>
?
```

try imap.googlemail.com instead of imap.gmail.com, also do you have imap enabled within your gmail account settings...it is required to be setup though gmail first...

---

### Post by karthick87 on 2010-06-18
Yes i have enabled IMAP in gmail...and also i have tried imap.googlemail.com


```
karthick@Ubuntu-desktop:~$ python ~/.Scripts/conkyEmail.py -c 60 --servertype=IMAP --servername=imap.googlemail.com --username=XXXX --password=XXXX --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.googlemail.com
    ssl: False
    username: XXXX
    password: XXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to IMAP server: imap.googlemail.com
*** ERROR:getIMAPEmailData:Unexpected error:  <class 'socket.error'>
?

```

---

### Post by kaivalagi on 2010-06-18
> **getyourkarthick said:**
> Yes i have enabled IMAP in gmail...and also i have tried imap.googlemail.com


```
karthick@Ubuntu-desktop:~$ python ~/.Scripts/conkyEmail.py -c 60 --servertype=IMAP --servername=imap.googlemail.com --username=XXXX --password=XXXX --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.googlemail.com
    ssl: False
    username: XXXX
    password: XXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to IMAP server: imap.googlemail.com
*** ERROR:getIMAPEmailData:Unexpected error:  <class 'socket.error'>
?

```

Try adding the --ssl option, I found with it it works quick, without I get timeouts too...

---

### Post by kaivalagi on 2010-06-18
Try adding the --ssl option, I found with it it works quick, without I get timeouts too...

---

### Post by karthick87 on 2010-06-18
```
karthick@Ubuntu-desktop:~$ python ~/.Scripts/conkyEmail.py --ssl -c 60  --servertype=IMAP --servername=imap.googlemail.com --username=XXXX --password=XXXX --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.googlemail.com
    ssl: True
    username: XXXX
    password: XXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to IMAP server: imap.googlemail.com
*** INFO: Searching for new mail on IMAP server: imap.googlemail.com
*** ERROR:getIMAPEmailData:Unexpected error:  <type 'exceptions.IndexError'>
?

```

---

### Post by kaivalagi on 2010-06-18
> **getyourkarthick said:**
> ```
karthick@Ubuntu-desktop:~$ python ~/.Scripts/conkyEmail.py --ssl -c 60  --servertype=IMAP --servername=imap.googlemail.com --username=XXXX --password=XXXX --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.googlemail.com
    ssl: True
    username: XXXX
    password: XXXX
    mailinfo: 0
    verbose: True
*** INFO: Logging on to IMAP server: imap.googlemail.com
*** INFO: Searching for new mail on IMAP server: imap.googlemail.com
*** ERROR:getIMAPEmailData:Unexpected error:  <type 'exceptions.IndexError'>
?

```

The password includes you @gmail.com yes?

I am stumped, it's working for me just fine using gmail???

I also think you are using an old version of the script thanks to conkycolors, I would suggest you install the latest version of conkyEmail from the ubuntu repos as per the first post instructions. Some of the logging output doesn't have as much detail as I am seeing (looks like the script you are using is from before 2009...?)

---

### Post by karthick87 on 2010-06-18
I have installed conkyEmail from the repos,and i have executed the above command..Now it works :)


```
karthick@Ubuntu-desktop:~$ python ~/.conkycolors/scripts/conkyEmail.py -c 60  --servertype=IMAP --servername=imap.googlemail.com --username=XXXX --password=XXXX --ssl --mailinfo=4 --verbose
*** INITIAL OPTIONS:
    servertype: IMAP
    servername: imap.googlemail.com
    port: None
    folder: Inbox
    ssl: True
    username: XXXX
    password: XXXX
    template: None
    mailinfo: 4
    maxwidth: 80
    linelimit: 0
    quote: "
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Logging on to IMAP server: imap.googlemail.com
INFO: Searching for new mail on IMAP server "imap.googlemail.com" in folder "Inbox"
INFO: Logging of from IMAP server: imap.googlemail.com
0

```Thank you so much :) and pls tell me how often it will check for new mails..?

---

### Post by kaivalagi on 2010-06-18
No probs, that conkycolor stuff out there really has caused issue after issue...it's always best to install the scripts using the repos as they are the latest versions available and any peculiar issues should be addressed

The interval for checks is up to you, when you setup the checking in your conkyrc file the interval is defined in the execi call, e.g. the following is every 600 seconds or 10 minutes:

```
${execi 600 conkyEmail -c 60  --servertype=IMAP --servername=imap.googlemail.com --username=XXXX --password=XXXX --ssl --mailinfo=4
```

Note that you can call the repo based install like above without any path or python command prefix

Have fun!

---

### Post by karthick87 on 2010-06-18
> **kaivalagi said:**
> No probs, that conkycolor stuff out there really has caused issue after issue...it's always best to install the scripts using the repos as they are the latest versions available and any peculiar issues should be addressed

The interval for checks is up to you, when you setup the checking in your conkyrc file the interval is defined in the execi call, e.g. the following is every 600 seconds or 10 minutes:

```
${execi 600 conkyEmail -c 60  --servertype=IMAP --servername=imap.googlemail.com --username=XXXX --password=XXXX --ssl --mailinfo=4
```Note that you can call the repo based install like above without any path or python command prefix

Have fun!

Thank you but it doesn't check mails in folders :(

---

### Post by kaivalagi on 2010-06-18
> **getyourkarthick said:**
> Thank you but it doesn't check mails in folders :(

Run "conkyEmail -h" in a terminal, and look at the folder option...you could run several of these checks in one conkyrc, each one with the correct folder name you need.

---

### Post by karthick87 on 2010-06-18
I mean label,i have created a label and i have applied filter for particular email address to this label..

---

### Post by karthick87 on 2010-06-18
Can you  pls post your conky script..?

---

### Post by kaivalagi on 2010-06-18
> **getyourkarthick said:**
> Can you  pls post your conky script..?

No, I don't use my own email script anymore, if you look I've created quite a lot of scripts...I only use the forecast script these days, and music is mpd based so no script needed....

You have to learn this stuff and figure it out, just get your head into it and you'll get it!

---

### Post by karthick87 on 2010-06-19
Sometimes i used to here songs in Totem Player,so is there conky script for totem player..?

---

### Post by kaivalagi on 2010-06-19
> **getyourkarthick said:**
> Sometimes i used to here songs in Totem Player,so is there conky script for totem player..?

Never head of a script for totem sorry, worth searching though, you never know :)

As a side note nearly all my scripts provide for a template file for layout of output, this is required for the email script, just take a look at the example files included in the install under /usr/share/conkyemail

There is a monster conkyrc thread on this site to give you lots of ideas here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Also check out the Conky Guide link in my sig

Hope that helps

---

### Post by kaivalagi on 2010-06-19
[COLOR="Red"]**[SIZE="4"]UPDATE[/SIZE]**[/COLOR]

[LIST]
[*]Updated to handle weird AOL mail issue
[*]Updated /usr/bin/ startup script to not used misused PYTHONPATH variable now
[/LIST]

New packages are now available from the ppa

---

### Post by karthick87 on 2010-06-19
Thank you :) and can you pls say me how to add pictures to my conky..Like the one you see in my attachment...

---

### Post by kaivalagi on 2010-06-19
> **getyourkarthick said:**
> Thank you :) and can you pls say me how to add pictures to my conky..Like the one you see in my attachment...

$image variable, take a look here:[http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")

From the above site:

***image	<path to image> (-p x,y) (-s WxH) (-n) (-f interval)***
Renders an image from the path specified using Imlib2.
Takes 4 optional arguments: a position, a size, a no-cache switch, and a cache flush interval.
Changing the x,y position will move the position of the image, and changing the WxH will scale the image.
If you specify the no-cache flag (-n), the image will not be cached. Alternately, you can specify the -f int switch to specify a cache flust interval for a particular image. Example: ${image /home/brenden/cheeseburger.jpg -p 20,20 -s 200x200} will render 'cheeseburger.jpg' at (20,20) scaled to 200x200 pixels. Conky does not make any attempt to adjust the position (or any other formatting) of images, they are just rendered as per the arguments passed. The only reason $image is part of the TEXT section, is to allow for runtime modifications, through $execp $lua_parse, or some other method.

---

### Post by karthick87 on 2010-06-19
> **kaivalagi said:**
> $image variable, take a look here:[http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

From the above site:

***image    <path to image> (-p x,y) (-s WxH) (-n) (-f interval)***
Renders an image from the path specified using Imlib2.
Takes 4 optional arguments: a position, a size, a no-cache switch, and a cache flush interval.
Changing the x,y position will move the position of the image, and changing the WxH will scale the image.
If you specify the no-cache flag (-n), the image will not be cached. Alternately, you can specify the -f int switch to specify a cache flust interval for a particular image. Example: ${image /home/brenden/cheeseburger.jpg -p 20,20 -s 200x200} will render 'cheeseburger.jpg' at (20,20) scaled to 200x200 pixels. Conky does not make any attempt to adjust the position (or any other formatting) of images, they are just rendered as per the arguments passed. The only reason $image is part of the TEXT section, is to allow for runtime modifications, through $execp $lua_parse, or some other method.


Thank you so much for answering all my questions :)

---

### Post by kaivalagi on 2010-06-19
That's okay, it looked as though you just needed to know where to look :)

---

### Post by vickoxy on 2010-08-06
Is it only me, but last few hours i have no conkyemail there checking my mail. I think it stopped after updating some files (see picture):

Any clue?

I am using 10.04 64bit and conkemail 2.08

---

### Post by kaivalagi on 2010-08-06
No idea, I'm not running Ubu. Does it run fine now?

---

### Post by vickoxy on 2010-08-06
> **kaivalagi said:**
> No idea, I'm not running Ubu. Does it run fine now?

No, not at all-it has to have something with the newest python update. I installed gnome-gmail-notifier and it is working ok.

So, who is now to ask for conkyemail support? Shame, i get used to have overview of all 4 accounts on desktop...

Or if it is python bug, maybe it will be fixed? Or is this maybe some new features disabling conkyemail to work...?

Thanks

---

### Post by vickoxy on 2010-08-07
Please ignore my last few posts- in the meantime, after few hours i have my conkyemail working again. Just like that-probably something with google, not with the python, although i am still suspicious about that last update.

Thanks :KS

---

### Post by kaivalagi on 2010-08-07
Any probs again post back and we can get to the bottom of it, hopefully...

---

### Post by vickoxy on 2010-08-07
> **kaivalagi said:**
> Any probs again post back and we can get to the bottom of it, hopefully...

Thanks :popcorn:

---

### Post by kaivalagi on 2010-08-08
[COLOR="Red"]**[SIZE="4"]UPDATE[/SIZE]**[/COLOR]

[LIST]
[*] Updated to handle timezones in received datatime for ordering
[/LIST]

New packages are now available from the ppa

---

### Post by sportsdude81 on 2010-08-12
How often does this check your email for new messages, and is there any way to adjust it.

---

### Post by sportsdude81 on 2010-08-12
> **sportsdude81 said:**
> How often does this check your email for new messages, and is there any way to adjust it.

nevermind i found in the thread.  my bad

---

### Post by kaivalagi on 2010-08-12
> **sportsdude81 said:**
> nevermind i found in the thread.  my bad
No worries, it's a conky thing, so is determined via the execi variables first parameter for anyone that doesn't know :)

---

### Post by sportsdude81 on 2010-08-13
Thanks for the feed back.  Got another question for you. Is there anyway to get audible notification when ever there is a new email.  I can right my python script if necessary.  Just was wondering if it was possible.  Not really sure how to go about it.

---

### Post by kaivalagi on 2010-08-13
> **sportsdude81 said:**
> Thanks for the feed back.  Got another question for you. Is there anyway to get audible notification when ever there is a new email.  I can right my python script if necessary.  Just was wondering if it was possible.  Not really sure how to go about it.

ALready answered in this thread before, post numbers 321 to 324 :)

Cheers

---

### Post by sportsdude81 on 2010-08-17
> **kaivalagi said:**
> ALready answered in this thread before, post numbers 321 to 324 :)

Cheers

Haha. I really need to look at threads better.  Thanks for your help

---

### Post by vickoxy on 2010-08-18
Well, i admit-i didn´t read all posts:redface: but i have to ask: is it possible to add in conky some simple line displaying only _hotmail unread_ messages?

Thanks

---

### Post by kaivalagi on 2010-08-18
> **vickoxy said:**
> Well, i admit-i didn´t read all posts:redface: but i have to ask: is it possible to add in conky some simple line displaying only _hotmail unread_ messages?

Thanks

Hotmail not supported sorry...too much of a pain in the backside. You're better ditching it in my opinion for something much more up-to-date and useful like gmail. The only reason I still have a hotmail account is for junk mail, M$ can have all the cr4p :)

---

### Post by vickoxy on 2010-08-20
No big deal-thanks, i use 4 gmail accounts, but my wife has one hotmail account an i am adjusting ubuntu for her...

Thanks

---

### Post by kaivalagi on 2010-08-21
> **vickoxy said:**
> No big deal-thanks, i use 4 gmail accounts, but my wife has one hotmail account an i am adjusting ubuntu for her...

Thanks

Get her on gmail too and auto-forward all hotmail messages to her new gmail account!

---

### Post by kartabosh on 2010-09-26
i will post on the thread but give you a copy as well since you know more than others

wish i could store conkyEmail to a local variable so i don't have to use the script twice in the same second
```
${if_match ${execi 600 conkyEmail [...]}!=0}${color #FFFF99} email 1$alignr ${exec conkyEmail [...]}$color$else email 1 $alignr 0$endif
${if_match ${execi 600 conkyEmail [...]}!=0}${color #FFFF99} email 2$alignr ${exec conkyEmail [...]}$color$else email 2$alignr 0$endif
${if_match ${execi 600 conkyEmail [...]}!=0}${color #FFFF99} email 3$alignr ${exec conkyEmail [...]}$color$else email 2$alignr 0$endif

```
anyone know a nice workaround?
if i had a localvar i could

```

$localvar1=${execi 600 conkyEmail [...]}!=0}
$localvar2=${execi 600 conkyEmail [...]}!=0}
$localvar3=${execi 600 conkyEmail [...]}!=0}
${if_match $localvar1!=0}${color #FFFF99} email 1$alignr $localvar1}$color$else email 1 $alignr 0$endif
${if_match $localvar2!=0}${color #FFFF99} email 2$alignr $localvar2}$color$else email 2 $alignr 0$endif
${if_match $localvar3!=0}${color #FFFF99} email 3$alignr $localvar3}$color$else email 3 $alignr 0$endif
```

that way it wouldn't abuse the imap server request thing, it would work only locally sending just one request

---

### Post by kaivalagi on 2010-09-26
Why not call the script like this in :

```
${execi 600 conkyEmail ...options... > /tmp/email1.txt
```

Then you can have another script to check for the right contents and "cat" the output is desired, which can then be output in conky like this:

```
${exec**p**i 600 /path/to/custom/script.sh}
```

It's not hard to do if you're a linux scripting noob with a little googling, the first bit is easy, just execi the output to a file with ">" as I showed.

The second part could be done using "sed", if you tell the script to output mailinfo too there will be more than one line if mail info is available, otherwise there will be only one line....or you could try to pattern match with regex in sed.

Saying this if you've never done any linux scripting and have never used regex is could be a lttle daunting and it may take some time, but if you persevere you should get there.

A good link for sed command help is here: [http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

Cheers

---

### Post by kartabosh on 2010-09-26
how would the script look like?

---

### Post by kaivalagi on 2010-09-26
> **kartabosh said:**
> how would the script look like?

That's for you to figure out...if I knocked something together it would take some time...

You may find good examples in the conkyrc thread here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Here's to start you on the right track

From the sed help link this will count the number of lines:

```
sed -n '$='
```

So for lines in a file from the first command in conky it would be like this:

```
cat /tmp/email1.txt | sed -n '$='
```

To get the result in a script to test you would have something like this:

```
#!/bin/sh
nooflines=`cat /tmp/email1.txt | sed -n '$='`

```

You'll need to get to grips with testing script variable contents etc, all of that sort of stuff is readily available via google

Good luck!

---

### Post by kartabosh on 2010-09-26
i couldnt show that screenshot in here because of personal information, thing is i want conky to print the email address and number of emails in another color
like 
no email: 
[email]email1@whatever.com[/email] 0 (white font)
[email]email2@whatever.com[/email] 0 (white font)
[email]email3@whatever.com[/email] 2 (yellow font)
[email]email4@whatever.com[/email] 0 (white font)
you get my point so the only way to do it is to test for new emails first 
if the answer is ? then display nothing, if it's a number different then 0 then color the line, so if i could dump the number of emails and then somehow insert it in the meantime (i'd need to insert it three times i guess, once when checking if it's 0 second checking if it's ? third actually displaying it)

---

### Post by kaivalagi on 2010-09-26
Best bet is a single script you call from conky using execpi, that you:

[LIST=1]
[*]put all the conkyEmail calls in
[*]then test the results and
[*]wrap output with ${color...} tags to suit
[/LIST]

I haven't seen any examples but the above suggestions along with you learning some linux scripting will get you there...don't expect a me to write the script for you though...you may get more help from the conkyrc thread I gave you a link for (not really relating to the email script itself, more conky manipulation)

---

### Post by kartabosh on 2010-09-26
i made it dump in email1 then i read it with 
exec cat /path/to/file

---

### Post by kaivalagi on 2010-09-27
> **kartabosh said:**
> i made it dump in email1 then i read it with 
exec cat /path/to/file

Which pretty much is the same as the script running as normal, are you sure you don't just want to call the script normally? It displays 0 or 1 or 2 etc for mail counts of each account used with it...

---

### Post by Sutur on 2010-10-19
Thanks for the script. I think I may have found a bug, though it's more likely I did something wrong.

Installed via repo.

```
surt@muspell:~$ conkyEmail --servertype=IMAP --servername=imap.googlemail.com --ssl --username=XXX@gmail.com --password=XXX --mailinfo=3

ERROR: getIMAPEmailData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 394, in getIMAPEmailData
    imap.login(username, password)
  File "/usr/lib/python2.6/imaplib.py", line 500, in login
    raise self.error(dat[-1])
error: [ALERT] Invalid credentials (Failure)

?

```

Can you shed any light on this please?

---

### Post by kaivalagi on 2010-10-20
> **Sutur said:**
> error: [ALERT] Invalid credentials (Failure)
Can you shed any light on this please?

...try variations on the login, maybe switching googlemail.com to gmail.com for the server? The error is coming from the imap libraries in python which are just fine so it must be a legitimate login failure...

---

### Post by kaivalagi on 2010-10-25
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to use the Python2 sym link instead of Python as Python3 is either here (Arch) or coming (Ubuntu)
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyemail_2.11_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyemail_2.11_source.changes)

The apt packages should be available soon

Cheers

**[COLOR="Red"][SIZE="3"]Note For 10.10 Users[/SIZE][/COLOR]**
I do beleive that Ubuntu 10.10 has a bug not having the python2 symbolic link, all other distro's I've used including previous versions of Ubuntu do have a python2 sym link...chances are it's been forgotten about in the hurry to rollout 10.10....

To fix things so the script can work as it is supposed to post the latest update just add a symbolic link in for python2 like this:
```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

---

### Post by diabolicalangle on 2010-10-28
I'm not sure if it's just me, but if there are more than 7 messages, the script messes up and shows some random number such as 21.

---

### Post by kaivalagi on 2010-10-28
Just marked 12 emails as unread ran it all is fine with or without the subject line (--mailinfo) output...:confused:

What do you see when running it with the --verbose option on the command line?

---

### Post by diabolicalangle on 2010-10-28
Did some more testing, it appears it messes up only on my *priority inbox* activated account, and especially between when i have emails between 6 and 9. Or maybe its just a combination of non-prioritized emails with prioritized emails, and the chances of that happening increase with more emails. Ill do some more testing and post my results. 

*** INITIAL OPTIONS:
    servertype: POP
    servername: pop.mail.yahoo.co.uk
    port: None
    folder: Inbox
    ssl: False
    username: None
    password: None
    template: /home/(usrname)/.conkyEmail.template
    mailinfo: 0
    maxwidth: 80
    linelimit: 0
    quote: "
    verbose: True
    errorlogfile: None
    infologfile: None
INFO: Logging on to IMAP server: imap.googlemail.com
INFO: Searching for new mail on IMAP server "imap.googlemail.com" in folder "Inbox"
INFO: Logging of from IMAP server: imap.googlemail.com
INFO: Logging on to IMAP server: imap.googlemail.com
INFO: Searching for new mail on IMAP server "imap.googlemail.com" in folder "Inbox"
INFO: Logging of from IMAP server: imap.googlemail.com
INFO: Logging on to IMAP server: imap.googlemail.com
INFO: Searching for new mail on IMAP server "imap.googlemail.com" in folder "Inbox"
INFO: Logging of from IMAP server: imap.googlemail.com
${voffset 10}${font Terminus:style=Bold:size=9}${color3}email1 ${font}${color1}${alignr}${offset -5}0
${font Terminus:style=Bold:size=9}${color3}email2 ${font}${color1}${alignr}${offset -5}0
${font Terminus:style=Bold:size=9}${color3}email3 ${font}${color1}${alignr}${offset -5}12

---

### Post by kaivalagi on 2010-10-28
I am running a prioritised inbox too, all the 12 unread emails I output for were priority ones

If you could let me know exactly what situation brought problems I can potentially duplicate the problem and try to put a fix in for it

Cheers

---

### Post by diabolicalangle on 2010-10-31
I feel reallllly dumb right now. Finally caught my attention as to why it was happening. The script counts branched messages too, and I was not paying attention to that. 

No fix needed!

---

### Post by kaivalagi on 2010-10-31
Good stuff, thank's for letting me know

---

### Post by kaivalagi on 2010-11-21
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated the /usr/bin/ script to dynamically call the available python exec as /usr/bin/python is linked to Python 3 (Arch) or will be at some point (Ubuntu)
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyemail_2.13_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkyemail_2.13_source.changes)

The apt packages should be available soon

---

### Post by kaivalagi on 2010-12-14
**[COLOR="Red"][SIZE="3"]IMPORTANT NEWS[/SIZE][/COLOR]**

All the script packages have now been copied into the **Conky Companions PPA**. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this: 

```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*

```
Then follow the modified first post instructions for the scripts

[COLOR="Red"]**Script updates will only be published through this new ppa going forwards**[/COLOR]

---

### Post by donoterase on 2011-02-23
@ Kaivalagi

Thank you so much for this script. I have used several gmail scripts previous to trying this (based on RSS retrieval method) and I just had issues left right and centre with conky crashing and not responding.

I did however modify the script so that I didn't have to store the password in plain text (I used stored passwords via gnome-keyring). Appreciate the work.

---

### Post by kaivalagi on 2011-02-23
> **donoterase said:**
> I did however modify the script so that I didn't have to store the password in plain text (I used stored passwords via gnome-keyring). Appreciate the work.

Yeah, sector11 gave me the heads up...I'm away from home for work right now but once back I'll take a look at the #! posts and weigh up putting a change in or not...I guess I'd need to provide another script to add/update a password in the keyring too

Chimo

---

### Post by kaivalagi on 2011-02-26
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Added keyring functionality so no clear text passwords need to be used, use the conkyKeyring tool to set passwords 
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyemail_2.14_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkyemail_2.14_source.changes)

The apt packages should be available soon


[SIZE="3"]**Hints and Tips**[/SIZE]

Here's the help from conkyKeyring:
```
Usage: conkyKeyring [options]

Options:
  -h, --help            show this help message and exit
  -u USERNAME, --username=USERNAME
                        The username where the password will be stored
                        against, this is usually an email address or other
                        account identifier which is used for login purposes
  -p PASSWORD, --password=PASSWORD
                        The password to be stored safely, leave unset to
                        retrieve the password
  -d, --delete          If set the password associated with the username given
                        is deleted
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

As an example I setup my gmail account first off by assigning a password to it like so:

```
conkyKeyring -u USER@gmail.com -p PASSWORD
```

I then use the email script to get the email details as follows:

```
conkyEmail -m IMAP -s imap.gmail.com -u USER@gmail.com
```

If no -p/--password argument is given the password is expected to be in the keyring and an attempt to retrieve it is made...

Thanks to donoterase for getting the ball rolling, I hope my choice of approach works for everyone

Chimo

---

### Post by donoterase on 2011-02-26
@kaivalagi

Just saw your post over at #!, and just had a squizz at the changes you made. Elegantly done. Now we CAN all sleep better at night knowing our passwords are secured. *Pat on the back*. Thanks for mentioning me also :D

---

### Post by kaivalagi on 2011-02-26
> **donoterase said:**
> @kaivalagi

Just saw your post over at #!, and just had a squizz at the changes you made. Elegantly done. Now we CAN all sleep better at night knowing our passwords are secured. *Pat on the back*. Thanks for mentioning me also :D

You don't want to search about what people are saying w.r.t. python-keyring and the security concerns then lol...still better than clear text in a text file though :)

Hopefully that conkyKeyring script may be of use to some too, it should mean various scripts that people knock together for all sorts can use passwords without storing them too...

edit: it's nice to see someone who is not afraid to get stuck in and edit scripts, you had to have a mention :) If only more would "do" rather than just "request"...

---

### Post by donoterase on 2011-02-26
> **kaivalagi said:**
> You don't want to search about what people are saying w.r.t. python-keyring and the security concerns then lol...still better than clear text in a text file though :)

Hopefully that conkyKeyring script may be of use to some too, it should mean various scripts that people knock together for all sorts can use passwords without storing them too...

edit: it's nice to see someone who is not afraid to get stuck in and edit scripts, you had to have a mention :) If only more would "do" rather than just "request"...

Despite the security concerns, it makes a would be intruder's life that much more difficult. At least the script is evolving and progress is key eh!

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by pranavkaranjkar on 2011-05-14
I have a small problem. My password contains the character '$'. How should I write my password in my conkyrc file (--password=xxx$xxx)?
Please help. I have some other special characters too, but I guess that wont be a problem. Right now, I get login error if I run conky from terminal.

Also, how do I change my main conkyKeyring password. If I store my mail password in conkyKeyring then it asks me for my keyring password. Please help. I am new at ubuntu...

---

### Post by Sector11 on 2011-05-14
> **pranavkaranjkar said:**
> I have a small problem. My password contains the character '$'. How should I write my password in my conkyrc file (--password=xxx$xxx)?
Please help. I have some other special characters too, but I guess that wont be a problem. Right now, I get login error if I run conky from terminal.

Also, how do I change my main conkyKeyring password. If I store my mail password in conkyKeyring then it asks me for my keyring password. Please help. I am new at ubuntu...

Conky in interpreting the $ as the beginning of "${}"

```
TEXT
$
```
displays:
```
${}
```
but
```
TEXT
${exec echo '$'}
```
displays:
```
$
```

Now will --password=xxx${exec echo '$'}xxxx work or not I have no idea.

As for the keyring, I have the same problem, so I continue to use:

```
--password=xxxxxx
```

---

### Post by pranavkaranjkar on 2011-05-14
Also, is it possible to hide the 1st line of conkyemail output? (The line saying "0 new emails" or "x new emails" or whatever...
I just want to have the sender and subject line directly if I have a new email.
If that can't be done, please tell me how can I change the font size for text in the same line. I don't know why, but I am having trouble with that.

---

### Post by Sector11 on 2011-05-14
> **pranavkaranjkar said:**
> Also, is it possible to hide the 1st line of conkyemail output? (The line saying "0 new emails" or "x new emails" or whatever...
I just want to have the sender and subject line directly if I have a new email.
If that can't be done, please tell me how can I change the font size for text in the same line. I don't know why, but I am having trouble with that.

Did the password thing work?

Show me the line you use for conky Email, mine is:
${execi 90 conkyEmail --servername=xxxxxxxxxxx --servertype=POP --ssl --port=995 --username=xxxxxxxxxx --password=xxxxxxxxxx}${voffset 5}¿${voffset -5}${execi 90 conkyEmail --servername=xxxxxxxxxxx --servertype=POP --ssl --port=995 --username=xxxxxxxxxx --password=xxxxxxxxxx}
because all I want it the email count, nothing else.

I want to work with yours to see if I can get rid of the count line.

---

### Post by pranavkaranjkar on 2011-05-17
> **Sector11 said:**
> Did the password thing work?

Show me the line you use for conky Email, mine is:
${execi 90 conkyEmail --servername=xxxxxxxxxxx --servertype=POP --ssl --port=995 --username=xxxxxxxxxx --password=xxxxxxxxxx}${voffset 5}¿${voffset -5}${execi 90 conkyEmail --servername=xxxxxxxxxxx --servertype=POP --ssl --port=995 --username=xxxxxxxxxx --password=xxxxxxxxxx}
because all I want it the email count, nothing else.

I want to work with yours to see if I can get rid of the count line.

Mine is

${font Zegoe Light:pixelsize=12}${execpi 1800 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --ssl --username=xxx --password=xxx --mailinfo=3}${font}

I guess the (--mailinfo) gives you the actual subject and sender line. Maybe the author can suggest some changes in the python script using which we can get rid of the count. Oh, and the password thing that you suggested didn't work, I guess. Before doing that I was getting a '?' on the conky display, but then there was nothing (for new mail also)..

---

### Post by pranavkaranjkar on 2011-05-17
> **kaivalagi said:**
> You don't want to search about what people are saying w.r.t. python-keyring and the security concerns then lol...still better than clear text in a text file though :)

Hopefully that conkyKeyring script may be of use to some too, it should mean various scripts that people knock together for all sorts can use passwords without storing them too...

edit: it's nice to see someone who is not afraid to get stuck in and edit scripts, you had to have a mention :) If only more would "do" rather than just "request"...

but if I store my password in keyring, then when I dont provide the "-p" option in conkyemail, it asks me for my conkyKeyring password which is not good if I have conky in my startup. Can you please explain how can I get conkykeyring to work with conkyemail?

---

### Post by kaivalagi on 2011-05-17
> **pranavkaranjkar said:**
> but if I store my password in keyring, then when I dont provide the "-p" option in conkyemail, it asks me for my conkyKeyring password which is not good if I have conky in my startup. Can you please explain how can I get conkykeyring to work with conkyemail?

Sector 11 had/has the same issue...I don't and can't reproduce. I think it has everything to do with the distro you use and how it is setup for password keyrings...and not the script, the script uses the python-keyring library which does the biz...

If you can't get it to work then use -p....I am not sure how I can help

Install Arch Linux and you wont have the issue :)

---

### Post by Sector11 on 2011-05-17
> **kaivalagi said:**
> Sector 11 had/has the same issue...I don't and can't reproduce. I think it has everything to do with the distro you use and how it is setup for password keyrings...and not the script, the script uses the python-keyring library which does the biz...

If you can't get it to work then use -p....I am not sure how I can help

Install Arch Linux and you wont have the issue :)

I've tried everything I "know" and still can't get it to work.
Glad conkykeyring installs though or I'd have to run an older version of conkyEmail.

Not knowing Python I have no idea what to even look for. :(
That will change, hopefully, when I find a book.

Just had a thought but will require a question on the #! forums.  I will keep people advised here!

---

### Post by amsri on 2011-07-06
I use arch linux. I tried every combination of servername port --ssl etc but cannot make yahoomail work (i have a paid yahoomail plus subscription in UK). GMAIL Works. I only get the following error with yahoo:

ashu@ashu-laptop:~$ conky -c ~/.conkyemailtask/conkyrc
Conky: desktop window (a0001a) is subwindow of root window (14d)
Conky: window type - desktop
Conky: drawing to created window (0x1e00001)
Conky: drawing to double buffer
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: ''
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: '(GM'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'GMT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'UT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'Pac'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: ''
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'UT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'UT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getPOPEmailData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 374, in getPOPEmailData
    lines = pop.top(num+1,1)[1]
  File "/usr/lib/python2.7/poplib.py", line 297, in top
    return self._longcmd('TOP %s %s' % (which, howmuch))
  File "/usr/lib/python2.7/poplib.py", line 159, in _longcmd
    return self._getlongresp()
  File "/usr/lib/python2.7/poplib.py", line 135, in _getlongresp
    resp = self._getresp()
  File "/usr/lib/python2.7/poplib.py", line 124, in _getresp
    resp, o = self._getline()
  File "/usr/lib/python2.7/poplib.py", line 106, in _getline
    line = self.file.readline()
  File "/usr/lib/python2.7/socket.py", line 447, in readline
    data = self._sock.recv(self._rbufsize)
timeout: timed out


OR IF using --ssl --port=995

ashu@ashu-laptop:~$ conky -c ~/.conkyemailtask/conkyrc
Conky: desktop window (a0001a) is subwindow of root window (14d)
Conky: window type - desktop
Conky: drawing to created window (0x1e00001)
Conky: drawing to double buffer
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: ''
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: '(GM'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'GMT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'UT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'Pac'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: ''
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'UT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'UT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: ''
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: ''
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'UT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'GMT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'GMT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'GMT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'GMT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'GMT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'GMT'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getEmailData:Unexpected error when converting receive date to datetime:'NoneType' object has no attribute 'group'
ERROR: getPOPEmailData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 374, in getPOPEmailData
    lines = pop.top(num+1,1)[1]
  File "/usr/lib/python2.7/poplib.py", line 297, in top
    return self._longcmd('TOP %s %s' % (which, howmuch))
  File "/usr/lib/python2.7/poplib.py", line 159, in _longcmd
    return self._getlongresp()
  File "/usr/lib/python2.7/poplib.py", line 135, in _getlongresp
    resp = self._getresp()
  File "/usr/lib/python2.7/poplib.py", line 124, in _getresp
    resp, o = self._getline()
  File "/usr/lib/python2.7/poplib.py", line 367, in _getline
    self._fillBuffer()
  File "/usr/lib/python2.7/poplib.py", line 357, in _fillBuffer
    localbuf = self.sslobj.read()
  File "/usr/lib/python2.7/ssl.py", line 151, in read
    return self._sslobj.read(len)
SSLError: The read operation timed out

ERROR: getPOPEmailData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 374, in getPOPEmailData
    lines = pop.top(num+1,1)[1]
  File "/usr/lib/python2.7/poplib.py", line 297, in top
    return self._longcmd('TOP %s %s' % (which, howmuch))
  File "/usr/lib/python2.7/poplib.py", line 159, in _longcmd
    return self._getlongresp()
  File "/usr/lib/python2.7/poplib.py", line 135, in _getlongresp
    resp = self._getresp()
  File "/usr/lib/python2.7/poplib.py", line 128, in _getresp
    raise error_proto(resp)
error_proto: -ERR problem retrieving message.

MY recent /usr/share/conkyemail/example/conkyEmail.template is

${voffset 10}${font Terminus:style=Bold:size=9}${color3}Yahoo: ${font}${color1}[--servertype=POP --servername=pop.mail.yahoo.co.uk --ssl --port=995 --connectiontimeout=15 --username=xxxxxx --password=xxxxx --mailinfo=4]
${voffset 10}${font Terminus:style=Bold:size=9}${color3}Google: ${font}${color1}[--servertype=IMAP --servername=imap.googlemail.com --ssl --username=xxxx@gmail.com --password=xxxxx --mailinfo=4]

I tried with or without ssl, with or without --port=995, used pop.mail.yahoo.com and plus.pop.mail.yahoo.com and other combinations.

my conkyrc is attached.

---

### Post by kaivalagi on 2011-07-06
Looks like yahoo are doing things a little differently with their headers which is the reason for all the initial receive date parsing errors, but that wont break things it just means the script can't ensure things are shown in the right order...

The main issue here seems to be the timeout errors you are getting regardless of ssl or non ssl connections...for those try increasing the connection timeout value, currently set to 15 seconds...

---

### Post by KenJean on 2011-07-26
I was hoping someone else was having this problem because I can never be sure I'm not at fault.

The conkyEmail script works great in a variety of distros - I've gotten it to work from Jaunty through to Maverick, plus Debian Squeeze and even Puppy. However, I am having trouble with my IMAP account in Natty derivatives. I get the following error:

ERROR: getIMAPEmailData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 445, in getIMAPEmailData
    imap.shutdown()
  File "/usr/lib/python2.7/imaplib.py", line 252, in shutdown
    self.sock.shutdown(socket.SHUT_RDWR)
  File "/usr/lib/python2.7/socket.py", line 224, in meth
    return getattr(self._sock,name)(*args)
  File "/usr/lib/python2.7/socket.py", line 170, in _dummy
    raise error(EBADF, 'Bad file descriptor')
error: [Errno 9] Bad file descriptor

Wondering if there is a fix for this.

As I said, this same conky setup works perfectly in the other distros, but I get the above problem in Natty, Pinguy Natty, Mint 11, lubuntu, etc. - all the Natty based distros.

Gmail and POP3 work fine, however.

-KJ

Figured it out:
Edit the file /usr/share/conkyemail/conkyEmail.py
Comment out (or delete) the line that reads: imap.shutdown()
(This is Line 445 in the version I have)

Voila!

---

### Post by kaivalagi on 2011-07-28
Nice find although it is already commented out in the latest version 2.15 :confused:

Here's the previous code commit: [http://bazaar.launchpad.net/~conky-companions/+junk/conkyemail/revision/34](http://bazaar.launchpad.net/~conky-companions/+junk/conkyemail/revision/34)

Make sure you're up to date ;)

Cheers

---

### Post by KenJean on 2011-08-02
I figured as much. The version I'm getting through the repositories is still 2.14 - even as I speak.

Don't know how long it takes for them to update these things.

Many thanks for your good work though. Keep it up.

-KJ

---

### Post by GrouchyGaijin on 2011-10-22
I have a quick question.

Since my Gmail account was hacked, I've switched to another account and become a bit paranoid.

If I use the code:
```

${execi 60 conkyEmail --servertype=POP --servername=my-secure-server --username=my-username --password=my-password}

```

Am I connecting securely?  I like having my email count in conky but don't want my credentials or email floating around open for anyone to see.  Do I need to add something to this command to ensure it connects securely?  It looks like according to the read me at the start of this thread that I need to.

I'm using conkyMail 2.14

---

### Post by kaivalagi on 2011-10-22
> **GrouchyGaijin said:**
> I have a quick question.

Since my Gmail account was hacked, I've switched to another account and become a bit paranoid.

If I use the code:
```

${execi 60 conkyEmail --servertype=POP --servername=my-secure-server --username=my-username --password=my-password}

```

Am I connecting securely?  I like having my email count in conky but don't want my credentials or email floating around open for anyone to see.  Do I need to add something to this command to ensure it connects securely?  It looks like according to the read me at the start of this thread that I need to.

I'm using conkyMail 2.14

You need to use the SSL option (--ssl) of the script to enforce encryption of the connection made, this needs a mail service that supports it and may require using a custom port (--port=) too using another script option.

Hope that helps

---

### Post by GrouchyGaijin on 2011-10-22
> **kaivalagi said:**
> You need to use the SSL option (--ssl) of the script to enforce encryption of the connection made, this needs a mail service that supports it and may require using a custom port (--port=) too using another script option.

Hope that helps

Thanks for the quick reply.

When I use -e I still get a message count.  If I use --SSL I don't.
I *think* I'm setup to use a secure server since my hosting provider Siteground lists two options for server settings.  One with secure and one without.
The port they say to use is 995.

---

### Post by GrouchyGaijin on 2011-10-22
OK got it - I need to use:
```
conkyEmail --ssl --port=995  --servertype=POP...
```

NOT --SSL

I'm slow.

Thanks!!

---

### Post by kaivalagi on 2011-10-22
> **GrouchyGaijin said:**
> OK got it - I need to use:
```
conkyEmail --ssl --port=995  --servertype=POP...
```

NOT --SSL

I'm slow.

Thanks!!

-e and --ssl do the same thing, use either :)

---

### Post by scratch178 on 2011-11-25
hi im running mint 12 and i love conky,
but conkyemail doesn't work any more.

${execi 300 conkyEmail --servertype=IMAP --servername=imap.mail.com --username=my email --password=my password --ssl}

if i change imap to pop it is working, but it shows me all the emails in my inbox, 
i like to have imap so i only see the new messages.

im running conkyEmail 2.14

terminal output


$ conky
Conky: /home/dominik/.conkyrc: 17: config file error
Conky: desktop window (1000024) is subwindow of root window (15d)
Conky: window type - normal
Conky: drawing to created window (0x3000001)
Conky: drawing to double buffer
ERROR: getIMAPEmailData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkyemail/conkyEmail.py", line 445, in getIMAPEmailData
    imap.shutdown()
  File "/usr/lib/python2.7/imaplib.py", line 1187, in shutdown
    self.file.close()
  File "/usr/lib/python2.7/socket.py", line 282, in close
    self._sock.close()
AttributeError: 'NoneType' object has no attribute 'close'

---

### Post by kaivalagi on 2011-11-26
> **scratch178 said:**
> hi im running mint 12 and i love conky,
but conkyemail doesn't work any more.

Looks like an issue with the server to me, working just fine here:

```
]$ conkyEmail -m IMAP -s imap.googlemail.com -e -u *******@gmail.com -p ********* -i 5
5 New
1. YouTube: "Your Personal YouTube Digest - 25 Nov 2011"
2. Peter Tyson: "Winter Offers for Peter Tyson"
3. Linked.NET Users Group (LIDNUG) Group Members: "[15] new discussions, [25] new
   comments and [42] new jobs on LinkedIn"
4. Python Community Group Members: "[1] manager's choice, [12] new discussions,
   [28] new comments and"
5. british.gas@britishgas.co.uk: "Avoid an estimated bill - send us your meter
   reading today"
```

---

### Post by scratch178 on 2011-11-28
just tried it with an other mail adress --> same error.
a friend of mine has the same problem and he uses gmail

---

### Post by kaivalagi on 2011-11-28
> **scratch178 said:**
> just tried it with an other mail adress --> same error.
a friend of mine has the same problem and he uses gmail

Are you pointing at the right google server (imap.googlemail.com), using SSL (-e or --ssl option ) and using the full email address as the username? As I've done above? The script has not changed in a long time and is working fine

[COLOR="Red"]edit:[/COLOR]

> **scratch178 said:**
> 
conkyemail doesn't work any more.
.
.
im running conkyEmail 2.14


Just checked as for some reason version 2.14 is still the latest in deb packages when I fixed a known issue with Imap in v2.15:

```
conkyemail (2.15)

  * Fixed conkykeyring dependency issue with some debian systems (case sensitivity) 
  * Updated IMAP usage by stopping call to shutdown method whihc errors since py 2.7
```

For now please use the attached version of the script by copying it over the top of the one found here: /usr/share/conkyemail/conkyEmail.py

I still need to get a VM up and running for Ubuntu before I can update the package, I don't have the time right now, maybe next weekend...

---

### Post by GrouchyGaijin on 2011-11-28
It works on my IMAP.

---

### Post by scratch178 on 2011-11-28
thanks for the new script!!!
its working now

great

---

### Post by MeKino on 2011-12-06
Hi,

I have been trying to get this script working but so far without any success and I'm not sure why... I've looked through all the posts so far and have not seen a solution so I hope maybe you could offer some advice?

I have a virginmedia account which still uses the ntlworld address.

These are the settings obtained from virginmedia:
Receiving mail (IMAP4)
IMAP4 server name : imap.ntlworld.com
IMAP4 SSL : Enabled
IMAP4 port : 993
IMAP4 authentication : Enabled (or 'Password' on Macs)
IMAP4 username : Full e-mail address, e.g.,richard.branson@ntlworld.com
IMAP4 SPA (Secure Password Authentication) : Disabled

So I tried:
conkyEmail -u xxx -p xxx -m IMAP -s imap.ntlworld.com -o 993 -e -c 45 -i 3 -v
*** INITIAL OPTIONS:
servertype: IMAP
servername: imap.ntlworld.com
port: 993
folder: Inbox
ssl: True
username: xxx
password: xxx
template: None
mailinfo: 3
maxwidth: 80
linelimit: 0
quote: "
verbose: True
errorlogfile: None
infologfile: None
INFO: Logging on to IMAP server: imap.ntlworld.com
ERROR: getIMAPEmailData:Unexpected error:Traceback (most recent call last):
File "/usr/share/conkyemail/conkyEmail.py", line 410, in getIMAPEmailData
  imap.login(username, password)
File "/usr/lib/python2.6/imaplib.py", line 500, in login
raise self.error(dat[-1])
error: [AUTHENTICATIONFAILED] Invalid credentials (Failure)

Any ideas?

Thanks in advance.

---

### Post by kaivalagi on 2011-12-06
Looks good to me, use gmail is my answer :)

I assume you can access via IMAP in a mail client such as Thunderbird using the same settings?

---

### Post by MeKino on 2011-12-07
As you say, there is nothing obviously wrong.

I don't use a mail client anymore on my pc\laptop - it's more convenient to log in via the web - but I might give it a try.

Thanks anyway.

---

### Post by kaivalagi on 2011-12-17
**[COLOR="SeaGreen"]UPDATE[/COLOR]**
A new conkyemail package is on it's way just to bring the package in-line with the recent fixes posted here relating to IMAP issues, changes are here: [https://launchpadlibrarian.net/87770195/conkyemail_2.15_source.changes](https://launchpadlibrarian.net/87770195/conkyemail_2.15_source.changes)

---

### Post by yaddoshi on 2012-09-22
> **pranavkaranjkar said:**
> but if I store my password in keyring, then when I dont provide the "-p" option in conkyemail, it asks me for my conkyKeyring password which is not good if I have conky in my startup. Can you please explain how can I get conkykeyring to work with conkyemail?

> **kaivalagi said:**
> Sector 11 had/has the same issue...I don't and can't reproduce. I think it has everything to do with the distro you use and how it is setup for password keyrings...and not the script, the script uses the python-keyring library which does the biz...

If you can't get it to work then use -p....I am not sure how I can help

Install Arch Linux and you wont have the issue :)

I'm surprised this question hasn't been properly answered yet.  Just in case someone else runs into this problem, I'm running Debian Squeeze and I resolved it by 1) using the _same password_ for python-keyring as my user account password and then 2) installing the **python-keyring-gnome** backend so that Gnome passes the user password along to python-keyring during account sign-in.  This way when conkyEmail script calls the conkyKeyring script due to no password set in the command string:
```
{execi conkyEmail -u email@server.ext -s server.ext}
```
then conkyKeyring accesses python-keyring and python-keyring does not prompt for the keyring password.  Provided you have stored the account username and password properly with conkyKeyring everything should then work.

I resolved this by running each command with terminal and the -v (verbose) flag set so I could see the error messages when it failed.

I hope that makes sense and helps someone else in the same boat.

---

### Post by Sector11 on 2012-09-22
> **yaddoshi said:**
> I'm surprised this question hasn't been properly answered yet.  Just in case someone else runs into this problem, I'm running Debian Squeeze and I resolved it by 1) using the _same password_ for python-keyring as my user account password and then 2) installing the **python-keyring-gnome** backend so that Gnome passes the user password along to python-keyring during account sign-in.  This way when conkyEmail script calls the conkyKeyring script due to no password set in the command string:
```
{execi conkyEmail -u email@server.ext -s server.ext}
```
then conkyKeyring accesses python-keyring and python-keyring does not prompt for the keyring password.  Provided you have stored the account username and password properly with conkyKeyring everything should then work.

I resolved this by running each command with terminal and the -v (verbose) flag set so I could see the error messages when it failed.

I hope that makes sense and helps someone else in the same boat.

I don't use GNOME nor gnome-keyring so I couldn't get an answer.  But this will get and entry in Tips and Tricks at Conky PitStop.

Thank you for sharing your findings.
What desktop/window manager are using?  I run SID with dual sessions: OpenBox and Xfce.

---

### Post by mollystribe on 2012-09-25
Hi everyone, and thanks for all the helpful tips. I cannot seem to get the notifications on my conky for my gmail...

I am still getting the error:

**ERROR: getEmailData:Unexpected error when converting receive date to datetime:invalid literal for int() with base 10: 'GMT'**

I have followed all the advice on this thread as far as increasing connection timeout, updating the conkyemail script to 2.15. It is baffling me. It is not a difficult server to forward. It's just gmail. Any help would be appreciated.

```
${goto 46}${color0}${font Ubuntu:style=Bold:size=10}${execpi 1200 /usr/share/conkycolors/bin/conkyEmail -m IMAP -s imap.googlemail.com  -ssl 993 -u scottjw89@gmail.com -p dsmnTMP09 -ssl -i 20 -c 20}${color}${font}
${goto 65}${voffset -8}${color0}${font Ubuntu:style=Bold:size=8}GMAIL${color}${font}
${goto 65}${voffset -4}${font Ubuntu:size=6}YOU HAVE ${execpi 1200 /usr/share/conkycolors/bin/conkyEmail -m imap -s imap.googlemail.com  -ssl 993 -u xxxx@gmail.com -p xxxx -i 20 -c 20} NEW MAIL(S)${font}

```

P.S. Running Linux Mint 13 - Mate desktop

---

### Post by kaivalagi on 2012-09-26
Looks like you have some unexpected email header info, maybe GMT instead of +0 in the date time received?

This is the code that transforms the text to a datetime, I added the bit in red to hopefully cope with GMT:

```
                        #extract timezone (strptime not supported) and convert it to a timedelta and add to datetime                        
                        timezonetext = matches.group(3).strip(" ")[COLOR="Red"]**.replace("GMT", "+0000")**[/COLOR]
                        timezonediff = timedelta(hours=int(timezonetext[0:3])) + timedelta(minutes=int(timezonetext[3:5]))

```

The script still works with this change but I couldn't reproduce your error and have a GMT date coming in, I think it is specific to one of your emails and not gmail...

Can you replace /usr/share/conkyemail/conkyEmail.py file with the one attached and let me know what happens?

---

### Post by mollystribe on 2012-09-26
> **kaivalagi said:**
> Looks like you have some unexpected email header info, maybe GMT instead of +0 in the date time received?

This is the code that transforms the text to a datetime, I added the bit in red to hopefully cope with GMT:

```
                        #extract timezone (strptime not supported) and convert it to a timedelta and add to datetime                        
                        timezonetext = matches.group(3).strip(" ")[COLOR="Red"]**.replace("GMT", "+0000")**[/COLOR]
                        timezonediff = timedelta(hours=int(timezonetext[0:3])) + timedelta(minutes=int(timezonetext[3:5]))

```

The script still works with this change but I couldn't reproduce your error and have a GMT date coming in, I think it is specific to one of your emails and not gmail...

Can you replace /usr/share/conkyemail/conkyEmail.py file with the one attached and let me know what happens?
Forgive my ignorance, but I have no idea where to place that code without a lot of the text showing up on the conky itself. Checking out the tar right now.

---

### Post by mollystribe on 2012-09-26
```
ERROR: getOutputData:Unexpected error:Traceback (most recent call last):
  File "/usr/share/conkycolors/scripts/conkyEmail.py", line 128, in getOutputData
    if count == -1:
UnboundLocalError: local variable 'count' referenced before assignment
```

With new conky script... and the gmail is not showing any numbers... WAS showing a "?" but now that is gone as well.

---

### Post by al1en on 2013-05-14
I cant get it to work with hotmail/live account. Works only with Gmail.
With hotmail setting I get only ? display

Im using xfce4 xUbuntu 13.04

---

### Post by GrouchyGaijin on 2013-05-23
I'm not sure if this thread is still open or not, but all of a sudden yesterday about 4:00pm my conkyemail script started crashing when connecting to my work exchange server through DavMail (local host connection).  The DavMail is working since I can still connect to Exchange via Thunderbird, but the Conky email script is really flaky now.
It will only show one message in the inbox and not list anything except the first message.
I can get the messages to show up if I enter the settings for a POP server, but then I have to move the messages since the POP part of the script doesn't support the number of read/unread messages.
Has anyone else seen had this happen?

---

### Post by al1en on 2013-05-25
For microsoft's live.com service i get the total messages instead of new ones.
Is there a way i can fix this?

---

