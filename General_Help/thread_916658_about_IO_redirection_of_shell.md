---
title: "about I/O redirection of shell"
date: 2008-09-11
forum: General Help
---

### Post by honglou on 2008-09-11
Hello.
I am getting a problem while testing the command below:

ls > ls_result.txt

I checked the file ls_result.txt and found there was a line of "ls_result.txt" there.I am confused.And my problem is:

Why the newly created file "ls_result" would get the line of itself's name inside?

Am i clear? My terminal results are below.

1.Before the command "ls > ls_result"

[FONT="Arial Narrow"]honglou@Huizhj-HL:~/bin2/bin3$ ls
file1  file2  file3
honglou@Huizhj-HL:~/bin2/bin3$[/FONT]

2.After the command "ls > ls_result",
while commanding "less ls_result.txt",I get this information below.Please notice that last line(red color).

[FONT="Arial Narrow"]honglou@Huizhj-HL:~/bin2/bin3$ less ls_result
file1
file2
file3
[COLOR="Red"]ls_result[/COLOR][/FONT]

Thank you!

---

### Post by iaculallad on 2008-09-11
That would just be normal since you are listing the contents thus it automatically adds the filename to the file you're trying to pipe the output to.

---

### Post by honglou on 2008-09-11
> **iaculallad said:**
> That would just be normal since you are listing the contents thus it automatically adds the filename to the file you're trying to pipe the output to.

Hi,iaculallad!
It's ok while thinking your way.But what confusing me is about the operation order there.Let's see.

While commanding "ls > ls_result",I guess the order would be:
1."ls" to tell the shell list the PWD to the standard output.So everything would be there without the name of the file "ls_result" which doesn't exist atm.
2. and "> ls_result" tells the shell to redirect the output from standard output to the file ls_result.
3.and the problem comes.

Thank you!

---

### Post by iaculallad on 2008-09-11
The logic might be like this (I may be mistaken):

-Upon issuing the command ls w/o any redirection would only list the content of the current folder location to the standard output, but, including a redirection (> ls_result) to a file would be interpreted by ls as a single command. Meaning, it would automatically create the file on the current directory at the same time appending the filename to the redirection file without displaying it on standard output.

---

### Post by Habbit on 2008-09-11
The redirection is always interpreted by the shell, not by ls or other commands (some commands like wget have a -o switch to avoid using redirections, for example). What is happening is that:[LIST=1]
[*]The shell parses your input line and notices that you want to redirect the output of ls to "ls_result.txt".
[*]The shell creates "ls_result.txt" and opens it for writing
[*]The shell invokes ls with its output stream redirected to "ls_result.txt"
[*]Ls makes a listing of all the files in the directory (which now include ls_result.txt) and writes it to _its_ standard output (which is now redirected to ls_result.txt).
[/LIST]In particular, if you did "ls -l" I don't know what size would show in "ls_result.txt": I suppose it would depend on how long the directory listing was and if the buffer would have already been flushed when ls got to the results file.

---

### Post by honglou on 2008-09-11
> **iaculallad said:**
> The logic might be like this (I may be mistaken):

-Upon issuing the command ls w/o any redirection would only list the content of the current folder location to the standard output, but, including a redirection (> ls_result) to a file would be interpreted by ls as a single command. Meaning, it would automatically create the file on the current directory at the same time appending the filename to the redirection file without displaying it on standard output.

Hi,iaculallad.Thanks a lot.
I agree you.Guess the shell is not quite logically defined.But I do appreciate the shell language.I am learning the shell recently.And it's great.

And I get a new concept "cloud computing" today while surfing the web.It reveals a splendid future for the coming net living.But I guess the shell language is the first step for me to talk to the "computer" thing at the moment.:)

Thanks for your kindness.Nice wishes to you.And by the way,I appreciate your signature very much.:)

---

### Post by honglou on 2008-09-11
> **Habbit said:**
> The redirection is always interpreted by the shell, not by ls or other commands (some commands like wget have a -o switch to avoid using redirections, for example). What is happening is that:[LIST=1]
[*]The shell parses your input line and notices that you want to redirect the output of ls to "ls_result.txt".
[*]The shell creates "ls_result.txt" and opens it for writing
[*]The shell invokes ls with its output stream redirected to "ls_result.txt"
[*]Ls makes a listing of all the files in the directory (which now include ls_result.txt) and writes it to _its_ standard output (which is now redirected to ls_result.txt).
[/LIST]In particular, if you did "ls -l" I don't know what size would show in "ls_result.txt": I suppose it would depend on how long the directory listing was and if the buffer would have already been flushed when ls got to the results file.


Thank you!It's clear now.:)
"May the source be with you!":)
And thank you for your nice wishes.:lolflag:

---

