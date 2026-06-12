---
title: "How to create a batch file to run a python script"
date: 2008-10-21
forum: General Help
---

### Post by asnast on 2008-10-21
Hello

I'm kinda new to unix systems and basically I got a python script which runs if i type "python /home/user/Desktop/nosy.py" (the path to the script.

I'd like to create a batch file and place in my path environment so that i can run the script just by typing  "nosy" from the shell.

Thanks, Alex Snast

---

### Post by geirha on 2008-10-21
You don't need a "batch" script for that (it's called shell script in linux btw, batch script is a dos/windows thing). 

1. Make the first line read
```
#!/usr/bin/env python
```
That's called the [shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)")

2. Make the script executable, either by right-clicking it, selecting properties and then check the executable flag under the permissions tab, or by typing in a terminal:
```
chmod +x /home/user/Desktop/nosy.py
``` After this you can also simply double-click it to run it btw.

3. Put it somewhere in the PATH. If all users should be able to run it, put it in /usr/local/bin. If only your user should run it, put it in ~/bin
```
sudo mv /home/user/Desktop/nosy.py /usr/local/bin/nosy
# or
cp ~/Desktop/nosy.py ~/bin/nosy

```

---

### Post by asnast on 2008-10-21
Thanks for your help however that doesn't work for me.

Here's the script:

#!/usr/bin/env python



import glob,os,stat,time



def checkSum():

    ''' Return a long which can be used to know if any .py files have changed.

    Only looks in the current directory. '''

    val = 0

    for f in glob.glob ('*.py'):

        stats = os.stat (f)

        val += stats [stat.ST_SIZE] + stats [stat.ST_MTIME]

    for f in glob.glob ('*.kid'):

        stats = os.stat (f)

        val += stats [stat.ST_SIZE] + stats [stat.ST_MTIME]



    return val


def main():
    
    val=0

    while True:

        if checkSum() != val:

            val=checkSum()

            os.system ('nosetests')

        time.sleep(1)

if __name__ == '__main__':
    main()

I'm getting: No such file or directory

Any ideas?

Alex Snast

---

### Post by asnast on 2008-10-21
Scratch that.

I got it sorted

---

