---
title: "[SOLVED] Thunderbird+ terminal help"
date: 2008-11-28
forum: General Help
---

### Post by cashman04 on 2008-11-28
So I have a weird one for my first post ever.

I trying to set up button at work to put on our desk that will send an email to me when pressed- alerting me we have a customer. I have most of this worked out, except I can't get the email to send from terminal.  I can make it generate the address and subject, but I cant figure out how to make it send other than somone sitting there and hitting the send key, which doesnt help me.  

The command I am using is

thunderbird mailto: [email]generic@email.com[/email]?Subject="You have a customer"

This opens up a compose window, and fills in the TO and SUBJECT fields,

IS THERE A COMMAND TO SEND THIS ALSO????????

I cant find anything on it.  Everything points to using mutt, or mailx or something.  I unsuccessfully tried these.  I just want to be able for it to send that message that it composes.

Since there is no real way to set up macros in ubuntu, my best bet is to be able to make this all in a single line in terminal. 

Please tell me if you know how to get this to work, and if i'm a complete idiot for trying.  

       Thanks in advance, 
                      Dan

---

### Post by NT4usB on 2008-11-29
If there were a way to imulate the key commands Ctrl+Enter in the terminal. That would send it. 
Other than that, I dunno.
Cool, different way to sent email though. First I've heard of this one.

---

### Post by cashman04 on 2008-11-29
If there is a way to do a Control+Enter in terminal, I can't find it.  If i could even find a simple macro program for linux, I could get it to work.

---

### Post by wd5gnr on 2008-11-29
Why use thunderbird?

Why not use one of the many "send mail" programs such as mail (I think that's in the mailx package)? I don't normally keep these installed on my desktop but I do on the servers and it would be easy enough to install them.

Oh. And as for "Macros for Linux" read [http://www.hotsolder.com/2008/08/autohotkey-for-linux-sort-of.html](http://www.hotsolder.com/2008/08/autohotkey-for-linux-sort-of.html)

---

### Post by cashman04 on 2008-11-29
I didn't want to mess around with figuring out how to configure mailx or mutt or any of those.  I just want a simple keystroke to run a single command and send a simple email.

I'm playing with xmacro now.  It seems like it could work perfect for what i need.  Problem is, I can get it to record a macro, but what is the command for playing back that macro?????????  Where is the macro saved at so i can add a delay.  This is another program that i cant seem to find any clear instructions on...lol.

thanks for pointing out xmacro though

---

### Post by cashman04 on 2008-11-29
Ok, well I figured it all out, but the easy part. 

Basically i have 2 commands in terminal-

 thunderbird mailto:19139635204@tmomail.net?Subject="You have a customer"

and


cat test.macro | xmacroplay -d 100:

I have the thunderbird command tied to Control+2 through gconf-editor(also shows up under compiz.

The macro is tied to Control+1

The macro sends a Control+2, (which opens the compose window and fills in the address and subject).  Then it sends a Control+Return.  Then a Return.

The problem is, when i type in the command to run the macro in terminal, it all works fine.  

But when I assign it to a hotkey, it does nothing.  I can't find why.  it also doesnt work when i make a launcher.

Anyone know if certain things cant run from a hotkey?

Also, thanks again for the link to xmacro.

---

### Post by wd5gnr on 2008-11-29
xmacroplay is the playback command (see the example). How are you binding it to the macro key? Can you make a script and bind that to the key?

---

### Post by cashman04 on 2008-11-30
I figured it out.  I made it into a script and can that command from a hotkey.-

./mail

But all I had to do it put this command as a hotkey.

cat test.macro | xmacroplay -d 100:0

I was having trouble because when i put the command into the hotkey, it didnt work.  My other hotkey worked fine, this didn't.  I was trying to use Ctrl+1.  Finally on a whim, I changed it to Ctrl+9.  And it worked just fine.

And just so everyone has it, heres a really simple command set for xmacro.

To record a macro

xmacrorec2 >filename.macro

It will ask for a key to use as the stop- use Esc.

It will record everything you do, keypresses and mouse movement(i just edited out and mouse movement)

This will also record it to what name you decide.  

From there you can open it with a text editor, and edit out, or in anything you need.  Its easy to do.
It doesn't remember times, so if you need a delay, just add

Delay 1

Or however long you need.

Then to play use the command

cat filename.macro | xmacroplay -d 100:0

And it will go from there.  What I did was went to gconf-editor
then -apps  then -metacity.  from there you can go to keybinding commmands, and input this string of text as a command.  then go up global keybindings, and change the hotkey for that command.  The only problem I had is some of the keys didnt seem to want to work.

I don't know how to but you can put this on SOLVED

Thanks.

---

### Post by whitethorn on 2008-11-30
at the top of the page, there's a menu called 

thread tools

click on that then something like Mark this thread as solved.

---

### Post by wd5gnr on 2008-12-01
> **cashman04 said:**
> I
cat test.macro | xmacroplay -d 100:0


cat filename.macro | xmacroplay -d 100:0



You ought to be able to use:

xmacroplay -d 100:0 <test.macro

and 

xmacroplay -d 100:0 <filename.macro

Slightly more efficient although obviously either will work.

---

### Post by cashman04 on 2008-12-02
> **wd5gnr said:**
> You ought to be able to use:

xmacroplay -d 100:0 <test.macro

and 

xmacroplay -d 100:0 <filename.macro

Slightly more efficient although obviously either will work.

Ah.  I didn't know you could do it that way.  Whats the difference in the 2?
I have noticed that sometimes, the command i was using doesn't like to work from a hotkey.

---

### Post by wd5gnr on 2008-12-03
when you write:

cat foo | bar

The shell spawns two subprocess: cat and bar. The cat program then reads the foo file and sends it to its standard output which is tied to bar's standard input (by virtue of |).

When you say:

bar <foo

The shell spawns one subprocess: bar and ties the foo file to its standard input. 

So it is one less process and some less overhead. In general it probably doesn't matter unless you like being pedantic.

---

