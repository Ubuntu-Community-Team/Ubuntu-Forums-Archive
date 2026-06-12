---
title: "howto BASH 3 commands? I wish to move a file to a different folder with bash script"
date: 2008-08-06
forum: General Help
---

### Post by adhg on 2008-08-06
Hello Experts,

I was wondering if there's a way to run this script:
I have a file on my folder /home/adhg/Desktop/test/hello.txt and I wish to move it to a different location -folder on XP machine.

for this, I do the following steps:

1. smbclient //xp/myFolder -U adhg%mypassw
[I get the prompt of smb:\>  and I write ]
2. put /home/adhg/Desktop/test/hello.txt hello.txt   
3. exit

//this works just fine.

so...my question is this: how can I achieve all this with a script (bash) where I simply indicating the script name and it does all the work?

Thank you

---

### Post by kihjin on 2008-08-06
I don't have the ability to test this using smbclient, but the solution may be found in using a combination of pipes and functions. 

command | smbclient

This says to redirect all standard ouput from command to the standard input of smbclient.

echo "hello"

This prints "hello" to standard output which will display in your console.

echo "hello" | smbclient

Send "hello" to smbclient's standard input.

Because you may need to use two commands, I don't know if it would be sufficient to just do echo "hello\nexit". That may very well work.

Otherwise use a function...

command() {
echo hello.txt
echo exit
}

command | smbclient

Good luck

---

