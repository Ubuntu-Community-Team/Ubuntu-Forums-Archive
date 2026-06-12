---
title: "[SOLVED] spawn command"
date: 2008-08-20
forum: General Help
---

### Post by WallyWest on 2008-08-20
Very simply, searching through examples for using expect in a script I have come across numerous pieces of code that use the command "spawn". I have done a ton of google searching but just cant seems to find a package for it. I am not even sure a package is needed but I haven't been able to run the command. Here is one example I was looking at with spawn in it.

#!/usr/bin/expect #Where the script should be run from.


set timeout 20 #If it all goes pear shaped the script will timeout after 20 seconds.

set name [lindex $argv 0] #First argument is assigned to the variable name

set user [lindex $argv 1] #Second argument is assigned to the variable user

set password [lindex $argv 2] #Third argument is assigned to the variable password
[COLOR="Red"]
spawn telnet $name #This spawns the telnet program and connects it to the variable name[/COLOR]


expect "login:" #The script expects login

send "$user " #The script sends the user variable

expect "Password:" #The script expects Password

send "$password " #The script sends the password variable

interact #This hands control of the keyboard over two you (Nice expect feature!)

THanks,

---

### Post by ariel on 2009-06-22
guess you found that:

sudo apt-get install expect

- will give you the "expect" shell that includes the spawn command

---

