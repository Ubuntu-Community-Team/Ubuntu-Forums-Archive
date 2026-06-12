---
title: "g++ (gcc) noob questions"
date: 2008-08-16
forum: General Help
---

### Post by elasto1mania on 2008-08-16
Hi,

This may sound dumb but I will still ask.
Is g++ the same as c++ I've searched the net and found that g++ is gnu c++ compiler but I still don't know if the syntax is the same.
When compiling the code do g++ automatically make the dependencies (I mean in synaptic if i select a program it gives many libraries so if i make a program would i need to import them or i just write the code and the compiler will make this for me.
Do you suggest me this language or i should go with another language?
What compiler should i use if i would stick with this language?

---

### Post by 3rdalbum on 2008-08-16
I'm not a C or C++ programmer, but my understanding is that the language and syntax remains the same no matter what compiler you use. You still need to import the libraries at the top of your source file.

If you stick with C++, then G++ is the perfect match. There are other options, but for general purpose use G++ is fine. As far as suggesting another language, you'd have to tell us what sort of programs you want to write, whether you need fast execution speed, what you like about C++ and don't like about it.

---

### Post by Garratt on 2008-08-16
Due to a 19k filesize limit on these lame forums I am unable to link a decent pdf, but there are alot of online documentation on the subject for the moment i will copy and paste a few key paragraphs from the documents I got from uni.

you can probably do a serach for these 2 docs online:
Unix is a Four Letter Word and Vi is a Two
             Letter Abbreviation
               Christopher C. Taylor
                   August 1993
----------------------------------------------------------------
and
University of Hawaii at Manoa
College of Engineering
Mastering the VI editor
----------------------------------------------------------------
> 
The VI editor is a screen-based editor used by many Unix users. The VI editor has powerful features to aid programmers, but many beginning users avoid using VI because the different features overwhelm them. This tutorial is written to help beginning users get accustomed to using the VI editor, but also contains sections relevant to regular users of VI as well. Examples are provided, and the best way to learn is to try these examples, and think of your own examples as well... There's no better way than to experience things yourself.
-----------------------------------------------------------------
As far as I understand, so far... I havn't done much reading on it due to it being cert2 critera and i'm mostly concentrating on cert4 c++ and java :P
Gnome Terminal in Ubuntu is an emulator of the Unix terminal you get by hitting CTRL F1 (full-screen terminal). almost all unix terminals are the same some with slight variants, but mostly work the same.

Heres another part of a chapter:
> 
2.1 Overview
Unix is an operating system designed at AT&T for their own personal use. The
following electronic mail message from Dennis Ritchie may help explain who
was responsible for Unix.
From: [email]dmr@alice.att.com[/email] Dennis Ritchie
Subject: re: UNIX
Message-ID: [email]11613@alice.att.com[/email]
Date: 14 Nov 90 05:53:03 GMT
Organization: AT&T Bell Laboratories, Murray Hill NJ
I read,
    Looks like folks are now beginning to credit the development
    of UNIX to Kernighan and Ritchie, but I thought the principal
    investigators were *Thompson* and Ritchie. Did something change?
The differences between Kernighan Ritchie Thompson are real
but very subtle. We all look alike middle aged with scruffy
graying beards. Note these distinctions:
-- Kernighan is slimmest, Ritchie middlest, Thompson heaviest
    in body build
-- Ritchie got contacts a couple of years ago and so is the
    only current non-glasses wearer
-- Thompson wouldn't touch netnews with a pole, Kernighan
    secretly gets misc.invest and misc.taxes mailed to him,
    Ritchie reads it more than is good for him and occasionally
    contributes
-- Ritchie is the only one who has met five people who have
    appeared on David Letterman Penn, Teller, Rob Pike, Mayor Koch, and
    the guy who raised the biggest hog in Ohio
-- Kernighan has written ten times as much readable prose as has
    Ritchie, Ritchie ten times as much as Thompson. It's tempting
    to say that the reverse proportions hold for code, but
    in fact Kernighan and Ritchie are more nearly tied
    and Thompson wipes us both out.

         Dennis


> 
Through a wild4 series of events, Unix has become a standard operating system
for many. Why else would you be reading this?
2.1.1 Case sensitivity
Unix is case sensitive. This means that Unix distinguishes between uppercase
and lowercase letters, i.e. Bi and bi don't mean the same thing to Unix.


> 2.1.2 The shell
There are a number of different flavors" of Unix available today. By different
   flavors" I mean different command interpreters called shells which handle
your input in their own unique way. This manual covers the C shell only. Many
of the things found here will be identical with other shells, but don't count on
it. It is possible to determine which shell is in use by typing echo $SHELL. The
response for the C shell is bin csh which is what you should get. One other
popular shell is the Bourne shell which would respond with bin sh.
2.1.3 Command syntax
Unix commands begin with a command name, often followed by ags and ar-
guments some of which are optional. The generic syntax is:
     command   flags  argument1 argument2 ...
Normally the flags are preceded by a hyphen to prevent them from being inter-
pretend as a filename. For example, in the command line
     ls -l avhrr
ls is the program called, -l is the flag, and avhrr is the argument. This command
tells the computer to list in long format the file called avhrr or, if avhrr is a
directory, to list all the files in the directory avhrr.


Hope that helps :D

Edit: for some reason my copy paste got rid of every fl fi out of each word, hopefully will not be a re-occurring theme with this system but anyway i edited as much as i could see by hand, if something doesn't quite make sence try putting a FL or FI in front of it :P

So far i know how to g++ excerise2.cpp -o exercise2   -to compile my scripts and 
./exercise2  -to run them :P

List - ls,  change directory cd, and thats about it :s

---

### Post by victor.zamanian on 2008-08-16
Hello elasto1mania!

g++ and c++ is in fact referring to the very same program: /usr/bin/g++-4.2
```
$ which c++
/usr/bin/c++

$ ls -l $(which c++)
lrwxrwxrwx 1 root root 21 2008-08-14 14:02 /usr/bin/c++ -> /etc/alternatives/c++

$ ls -l /etc/alternatives/c++
lrwxrwxrwx 1 root root 12 2008-08-14 14:02 /etc/alternatives/c++ -> /usr/bin/g++

$ ls -l /usr/bin/g++
lrwxrwxrwx 1 root root 7 2008-08-14 14:02 /usr/bin/g++ -> g++-4.2

$ ls -l /usr/bin/g++-4.2 
-rwxr-xr-x 1 root root 195260 2008-04-01 20:17 /usr/bin/g++-4.2
```
"->" means it's a symbolic link (like a shortcut) to the file on the right side of the "->". So that answers that, at least. :-)

Now, when it comes to using synaptic to install programs, what synaptic really does is install package files. Those package files contain not only the software, but information about what _other_ software that needs to be installed, if any, to run that program. So when you write your code, you don't worry about dependencies just yet, you just write your code and compile. Then when you've created your program, you can create a so called Debian package (.deb) (which is a problem for a whole other thread!) that holds the information regarding dependencies.

I would say most code for linux is written in C, traditionally. But there's nothing wrong with writing a program in C++ if the type of program you plan to create is more suited for that language. C I would think is a little more time efficient and C++ is a little more advanced (object oriented). I won't go into detail about the differences and areas of C and C++ because I would probably just tell lies here, because I just don't know enough about C++. :-) I suggest posting another thread, asking about the advantages/disadvantages of C/C++ or consulting Google about it.

I wish you luck, and remember: No question is a dumb question here on the UbuntuForums. ;-)

---

### Post by elasto1mania on 2008-08-16
Thx guys for helping. I will go on c++ .

---

### Post by elasto1mania on 2008-08-17
Hello victor.zamanian!

Didn't saw at first your post.
Trank you very much about explaining, now i actualyy understand how it works.
I will google the c/c++ an eventually post on the forums.
Thx again.

---

### Post by cmay on 2008-08-17
hi
there is also a programming talk section at this forum .
you can ask questions there too.

---

### Post by Garratt on 2008-08-17
Heeeeaps of good links on these sites, and tutorials:

[http://www.deitel.com/ResourceCenters]("http://www.deitel.com/ResourceCenters/ResourceCenterList/tabid/56/Default.aspx")

[http://www.codearchive.com/]("http://www.codearchive.com/")

personally i prefer Object oriented programming (OOP), it makes more sense for nubs who have not been in the programming game since day one, and reflects how we view the world in general, in my opinion OOP is the way to go these days anyway, due to so many oldschool c programmers out there, theres a bit more demand for c++ and Java work in OOP. I guess it just depends how your brain works, also another thing to consider is, alot of people get stuck in their ways, so make an informed descision(by researching) and decide which ways you want to get stuck in, eg using VI or using notepad > using c or c++ / java or pascal or watever.. while syntax is slightly different between things like c++ and java the principles are the same in OOP, most of the time in OOP you spend 90% planning the program then only 10% writting code, or 10% of the time copy pasting other peoples code. (why reinvent the wheel? it's fine the way it is)
:)

---

