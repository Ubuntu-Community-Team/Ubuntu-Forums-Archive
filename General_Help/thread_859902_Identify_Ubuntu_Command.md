---
title: "Identify Ubuntu Command"
date: 2008-07-15
forum: General Help
---

### Post by mthalis on 2008-07-15
How can i identify given input for the terminal Command or not using C language.

---

### Post by cyclobs on 2008-07-15
what do you mean exacually?

---

### Post by lisati on 2008-07-15
If you're using 'C', the "mysterious" argc & argv (as in int main(int argc, char *argv[]) can be useful. argc contains the number of "arguments" on the command line, and *argv[] is a list of pointers to what's on the command line. Most C compilers let you use argv[0] to figure out the name of the current running program.

---

### Post by mthalis on 2008-07-15
so i want when use give input for terminal, if that enter word is key word i want catch that words and execute them seperatly if not key word enter,i want print that word in terminal.

---

### Post by cyclobs on 2008-07-15
ok i'm no help, sorry

---

### Post by mthalis on 2008-07-15
just given word keyword or not plz.. help....

---

### Post by cariboo on 2008-07-15
You might get a little more help if you enter your quetions here:

[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

This forum is mostly for question about Ubuntu, not programing

Jim

---

### Post by jocko on 2008-07-15
I think you need to explain your problem better (and probably ask it in the programming subforum).
As it is now, I doubt anyone will understand what you are asking for (at least I don't, and I have no problems understanding english... I could be wrong, maybe a programmer will see what you want anyway...).
Try to describe exacly what you want to do. I'm sure I will not be able to help (not a programmer), but if what you want is possible I'm sure someone else can help you.

---

### Post by kaens on 2008-07-15
Does [this](http://www.d.umn.edu/~gshute/C/argv.html) help? You can check if a certain argument is a certain string with strcmp(), if I remember correctly.

---

### Post by lisati on 2008-07-15
mthalis: please clarify for us:

1. Do you want to check what was on the command line when your program is run, or do you want to get some input from the user while the program is running?
2. Is English your second language?

---

### Post by mthalis on 2008-07-15
English second language, i want to do simple thing
when you type word in terminal example "hello" i want to check weather it is keyword or not,let say type "ls" it is keyword likewise i want to know how can identify keyword using simple program if cant give me some help.

---

### Post by jocko on 2008-07-15
So you have some kind of list of keywords? and you want to know a command that can compare a word you type in a terminal with that list? Is that your question?
Otherwise you really need to explain it in more detail. Even if your english is poor (no offense), I think that's not the main reason why we don't fully understand your question.

---

### Post by mthalis on 2008-07-15
Yes that's what i want, list keywords

---

### Post by kaens on 2008-07-15
By keyword, do you mean any command that you can enter in the terminal?

Keywords: ls man wget bash ssh apropos apt-get
Not Keywords: barney dmj weoairj

?

---

### Post by mthalis on 2008-07-15
yes, you are write that what i want..

---

### Post by kaens on 2008-07-15
The shell variable $PATH contains all of what could be considered "keywords" in this sense. At a terminal, 

```

echo $PATH

```

will give you a list of directories that programs that are "keywords" reside in, seperated by the character ':'.

What you want to do is probably create a list of files under the directories in $PATH, and then check to see if the command-line argument(s) are present in that list. 

How to actually write that in C is left as an excersize for the reader, partially because I don't know C very well, and partially because this sounds a bit like homework - and even if it's not, figuring out how to do it yourself is a good excersize (I may write it myself in C when I have some spare time, just as a "learning-proper-C" excersize)

---

