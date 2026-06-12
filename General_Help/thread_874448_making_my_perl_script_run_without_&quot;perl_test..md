---
title: "making my perl script run without &quot;perl test.pl&quot;"
date: 2008-07-29
forum: General Help
---

### Post by LinuxNoob#1 on 2008-07-29
Hello everybody,  I am having trouble.  I have grown used to running perl scripts on my Solaris OS at work by just making the script executable and running it, and seeing magic take place with the wonderful language that is perl

On my Ubuntu system at home (my hobbie) I have been trying to get this to work. 

Here are the steps I took
1.  added the following code the my .bashrc
```
# add perl to $Path
export PATH=$PATH:/usr/bin/perl
```

sourced it, and received the following result
```
pbrack@pbrack-desktop:~/Documents$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/bin/perl
pbrack@pbrack-desktop:~/Documents$
``` 


2.  made sure I checked the perl path I entered looked right
```
pbrack@pbrack-desktop:/usr/bin$ cd /usr/bin | ls -la |grep perl
-rwxr-xr-x  1 root   root      24106 2007-11-27 03:05 find2perl
-rwxr-xr-x  1 root   root      70672 2007-10-09 14:42 foomatic-perl-data
-rwxr-xr-x  2 root   root      14056 2007-11-27 03:06 perl
-rwxr-xr-x  2 root   root      14056 2007-11-27 03:06 perl5.8.8
-rwxr-xr-x  1 root   root      37273 2007-11-27 03:05 perlbug
-rwxr-xr-x  1 root   root      17953 2007-11-27 03:05 perlcc
-rwxr-xr-x  1 root   root        224 2007-11-27 03:07 perldoc
-rwxr-xr-x  1 root   root        125 2007-11-27 03:06 perldoc.stub
-rwxr-xr-x  1 root   root      11937 2007-11-27 03:05 perlivp
pbrack@pbrack-desktop:/usr/bin$ 
```
3.  wrote my test.pl perl script to test theory
```
#!/usr/bin/perl

print "test\n";
```
4.  made my perl script executable
```
pbrack@pbrack-desktop:~/Documents$ chmod a+x test.pl
pbrack@pbrack-desktop:~/Documents$ ls -la |grep test
-rw-r--r--  1 pbrack pbrack   463 2008-01-21 19:40 testconversions.pl
-rwxr-xr-x  1 pbrack pbrack    33 2008-07-29 20:40 test.pl
-rw-r--r--  1 pbrack pbrack    32 2008-07-29 20:35 test.pl~
pbrack@pbrack-desktop:~/Documents$ 
```


when I try to run
```
test.pl
```
I get the following :

pbrack@pbrack-desktop:~/Documents$ test.pl
bash: test.pl: command not found
pbrack@pbrack-desktop:~/Documents$ 




Any suggestions?
:)

---

### Post by ashgromnies on 2008-07-30
You need to specify the path to it - that is, 
```

./test.pl
```

because if you just run `test.pl` it will try looking for it in your PATH.

---

### Post by sdennie on 2008-07-30
This isn't a perl problem but a path problem.  By default, the machine doesn't have "." in the path so, you'll have to say ./test.pl.  You can add "." to the path but, I prefer to make a ~/bin directory and add that to the path and stick my scripts in there so that I don't get any surprises when I type commands.

---

### Post by p_quarles on 2008-07-30
While /usr/bin/perl is in your path (you didn't need to do anything: it already was), the script itself isn't. You need to tell the shell to look in the present directory instead of the path:
```
./test.pl
```
Or the full file path:
```
/home/pbrack/Documents/test.pl
```
Should work. :)

---

### Post by knightcoder on 2008-07-30
Well, I don't understand why you're adding /usr/bin/perl to $PATH.
PATH has only the folders where it has to look for commands. /usr/bin/perl itself is a command in the folder /usr/bin.

So, remove it from the PATH and it'll work. Cos it did for me.

---

### Post by LinuxNoob#1 on 2008-07-30
Thanks guys,

That was very informative.  I really enjoy learning more about the OS.  I like the idea of creating a bin directory and adding that to the PATH.

---

