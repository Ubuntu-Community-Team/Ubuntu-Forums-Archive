---
title: "Scripting help, extracting data from file into multiple files"
date: 2008-11-19
forum: General Help
---

### Post by lotharz0r on 2008-11-19
Hi.
I've got a data file which contains data I must extract to multiple single files.
The data is seperated in this way:
useless dataasdjnas [B]BEGIN
data1
data2
data3
data4
END[/B] useless........
useless data I dont want
7ibasdlnj8kjbqw8tl [B]BEGIN
data1
data2
data3
data4
END[/B]

and so on.

So what I want to do is to extract BEGIN and everything from it to END and put it into one file, ignore the data I dont want that is between END and the next BEGIN, then extract from BEGIN to END into another file.
Basicly extract what I have put as bold in this post

Need some help with this please.

---

### Post by Portmanteaufu on 2008-11-19
That's easy enough. Before I post, though, what are you using this for if you don't mind my asking? It sounds like a homework assignment.

---

### Post by DGortze380 on 2008-11-19
> **Portmanteaufu said:**
> That's easy enough. Before I post, though, what are you using this for if you don't mind my asking? It sounds like a homework assignment.

x2


That is definitely easy enough to do with a Bash Script. 
We need a little more info though.

What is BEGIN and END? (ie. Whats the delimiter?)

What kind of data are you extracting? What is the format of the 'useless data' in between.

Last, is this an assignment? We aren't going to do your homework for you, but we'll be happy to give you some hints.

---

### Post by lotharz0r on 2008-11-19
Hehe, no, it is not an assignment
This is an .dat file which contains multiple vcards (contact info)
The file is an old backup of a contact list on a nokia mobile phone which I need to restore, because I have had some phone issues that caused a wiped contact list.
Nokias PC Suite cant do the job because its not in the format it expects.
So what I want to do is extract the data into multiple vcards and import them into outlook.
Then I can sync my mobile phone with outlook and all my contacts will be back

This is a direct copy of some of the lines in the file im working on (I have only edited the names and phone numbers):
[I]0        2               c   BEGIN:VCARD
VERSION:2.1
REV:20060721T132850Z
N:John Doe;;;;
TEL;CELL:4428228
END:VCARD
0        3               e   BEGIN:VCARD
VERSION:2.1
REV:20060721T132850Z
N:Jane Doe;;;;
TEL;CELL:9451555
END:VCARD[/I]

The useless data you see after END:VCARD and before BEGIN:VCARD is probably just a way nokia formats their contact list.

If i try copying:
[I]BEGIN:VCARD
VERSION:2.1
REV:20060721T132850Z
N:Jane Doe;;;;
TEL;CELL:9451555
END:VCARD[/I]


into one file and save it as .vcf I can import it into Outlook.


So this is not a homework assignment, Im just trying to get back my lost contact list.

---

### Post by lotharz0r on 2008-11-19
I have fiddled around with AWK, and I've got this, but I dont think I've got the regex right.
> # cat test.awk
BEGIN { inside=0; myfile=0}
/^.*BEGIN.*/ { inside=1; next; }
/^.*END.*/ { inside=0; myfile++; next;}
{if (inside) { print $0 >> myfile; }}


---

### Post by Portmanteaufu on 2008-11-19
Great, that sounds like a neat project. Here's a perl script that should do what you need it to do:

```

#!/usr/bin/perl
$printing = 0;
$outFileNumber = 0;
while($line = <STDIN>)
{
        if($printing == 1)
        {
                if($line =~ /(.*?\bEND)\b.*?$/)
                {
                        print OUTFILE $1."\n";
                        $printing = 0;
                        close OUTFILE;
                        $outFileNumber = $outFileNumber + 1;
                }
                else
                {
                        print OUTFILE $line;
                }
        }
        else
        {
                if($line =~ /.*\b(BEGIN\b.*?$)/)
                {
                        open OUTFILE, ">outFile".$outFileNumber.".vcf" or die "Couldn't open file for output: $!";
                        print OUTFILE $1;
                        $printing = 1;
                }
        }
}

```

Run it like so:

```
cat <file with all the data> | <name of script> 
```

It will create a separate file, one for each section of BEGIN/Data/END, titled outFile#.vcf, where the # is the order in which the section appeared in the data file.

If the regular expressions I used aren't exactly what you wanted, just tweak them. If you need help with doing that, just say the word.

---

### Post by lotharz0r on 2008-11-19
Excellent stuff Portmanteaufu!
I now got hundreds of .vcf files.
I will post a reply with the final results when I have done all the work in case you are interested.

Thanks a lot, you are a lifesaver

---

### Post by Idefix82 on 2008-11-19
I am sure that this can also be done with the sed command and would be quite interested if anyone can provide such a solution. I haven't touched sed yet, but I am trying to learn it slowly. For example
```
sed -n '/BEGIN/,/END/ p'<testfile
```
would print everything between BEGIN and END (but including the lines with BEGIN and END) onto the screen. This can probably be concatenated with awk to produce the desired result.

---

### Post by Portmanteaufu on 2008-11-19
> **lotharz0r said:**
> Excellent stuff Portmanteaufu!
I now got hundreds of .vcf files.
I will post a reply with the final results when I have done all the work in case you are interested.

Thanks a lot, you are a lifesaver

No problem! Glad it worked out for you! :D

---

