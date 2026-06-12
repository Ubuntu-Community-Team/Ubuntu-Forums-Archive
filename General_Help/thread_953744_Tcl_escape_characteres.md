---
title: "Tcl escape characteres"
date: 2008-10-20
forum: General Help
---

### Post by gustavolinux on 2008-10-20
Folks, I'm having a problem with a tcl escape character: the backslash.

I'm trying to create a script that calls another script. One of the parameters that is sent to the other script is a password (to use with ssh). Well, if the password is a usual string, like 'carrie', it works fine. The problem occurs when the first letter of the password is a dollar sign, like $testpass. When this password is used, tcl seems to write the string inside braces, like {$testpass}. This new value created by tcl is sent to the second script, and then my system fails, because the correct password is $testpass, and not {$testpass}.

Please, somebody that knows tcl can help me?

A simple teste code shows my problem:

---------
#!/bin/sh

package require Expect

set timeout 15

set ssh_password \$testpass

spawn ./ssh.sem.passw.sh 5622 root $ssh_password 172.21.1.2 md5sum /root/ipt-firewall
interact

--------

Debugging, I found that the parameters given to spawn by tcl engine was:

./ssh.sem.passw.sh 5622 root {$testpass} 172.21.1.2 md5sum /root/ipt-firewall

Where the incorrect password appears... It should be $testpass.

Thanks by the attention dudes...

---

### Post by gustavolinux on 2008-10-21
I'll make the test more simple, than I can explain it perfectly...

There is two files: teste.sh and ssh.teste.sh

teste.sh code is:

#-------------------------------
#!/bin/sh

package require Expect

set timeout 15

set ssh_password \$teste

spawn ./ssh.teste.sh $ssh_password
interact
#-------------------------------

and ssh.teste.sh is:

#-------------------------------
#!/usr/bin/expect -f
# set Variables

set timeout -1

log_user 0

send_user "\nTeste:\n"
send_user $argv
send_user "\n"
#-------------------------------


I save both in the same folder and type the following command:

tclsh ./teste.sh

The output that I get is:
---------------------------------------
spawn ./ssh.teste.sh $teste

Teste:
{$teste}
---------------------------------------

And it should be

Teste:
$teste

Hope you folks can reproduce now... Thanks by the attention...

---

