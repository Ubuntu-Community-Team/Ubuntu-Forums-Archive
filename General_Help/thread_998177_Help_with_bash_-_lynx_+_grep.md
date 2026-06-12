---
title: "Help with bash - lynx + grep"
date: 2008-11-30
forum: General Help
---

### Post by parm289 on 2008-11-30
I am trying to create a script that can be run in Conky to display the New York Jets opponent and score.  To do this, I'm using Lynx to get a text output of a webpage (specifically sports.espn.go.com/nfl/scoreboard) and greping to get the text I need.

By entering this into terminal:
```
lynx -nonumbers -dump sports.espn.go.com/nfl/scoreboard | egrep -i -A4 -B1 New\ York\ Jets
```

I get:
```
Denver (6-5, 3-2 away)
New York Jets (8-3, 4-1 home)
CBS
1 2 3 4



```

Now, thats the general info I need (the two empty lines below 1 2 3 4 will have the score by quarter for both teams - so I need those).  However, I want to format it in a special way for Conky.

Ideally, I'd want:
```
Denver (record)             _ _ _ _
New York Jets (record)      _ _ _ _
```
Where the underscores contain the information presented in the two lines under "1 2 3 4" and (record) is the stuff in the parens from before.

Therefore, to get this format, I'd have to eliminate the two lines:
```
CBS
1 2 3 4
```

So, what I have tried to do was write a test bash script, scores.sh.  This is my working script:
```
#!/bin/bash
OPP=`lynx -nonumbers -dump http://scores.espn.go.com/nfl/scoreboard | egrep -i -A0 -B1 New\ York\ Jets`
JETS=`lynx -nonumbers -dump http://scores.espn.go.com/nfl/scoreboard | egrep -i -A0 -B0 New\ York\ Jets`
VARA="\n 1\t2\t3\t4\n"
VARB="$JETS\nCBS\n1\t2\t3\t4"
SCORE=`lynx -nonumbers -dump http://scores.espn.go.com/nfl/scoreboard | egrep -i -A2 -B0 "$VARB"`
printf "$OPP"
#printf "\n$VARB"
printf "\n $SCORE"
```

The display that seemingly should result from this script is:
```
Denver Broncos (record)
New York Jets (record)



```

Where lines 3 and 4 are empty.  But, $SCORE returns no value when it should return two blank lines.  I imagine this has something to do with the variable pattern I am inputting into the command for $SCORE.

As you can probably tell, I'm new to bash and need some serious help.  What I want to eventually do is retrieve the 2 teams and the score, but not the lines between them (CBS and 1   2   3   4).  If anyone could help it would be much appreciated.

---

### Post by sdennie on 2008-11-30
Try something like:

```

#!/usr/bin/perl

use strict;

my $raw = `lynx -nonumbers -dump sports.espn.go.com/nfl/scoreboard | egrep -i -A4 -B1 New\\ York\\ Jets`;

my @lines = split /\n/, $raw;
$lines[0] =~ s/^\s+//;
$lines[1] =~ s/^\s+//;
print "$lines[0]		$lines[4]\n";
print "$lines[1]		$lines[5]\n";

```

---

### Post by parm289 on 2008-11-30
Thanks for the reply - I don't know perl, but I think I deciphered what your script does (can't believe I didn't think of something like that...).  Thanks a bunch!

---

### Post by sdennie on 2008-11-30
Actually, this produces nicer output:

```

#!/usr/bin/perl

use strict;

my $raw = `lynx -nonumbers -dump sports.espn.go.com/nfl/scoreboard | egrep -i -A4 -B1 New\\ York\\ Jets`;

my @lines = split /\n/, $raw;
$lines[0] =~ s/^\s+//;
$lines[1] =~ s/^\s+//;

format STDOUT =
@<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<< @>>>>>>>>>
$lines[0]                         $lines[4]
@<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<< @>>>>>>>>>
$lines[1]                         $lines[5]
.

write STDOUT;

```

;)

---

### Post by geirha on 2008-11-30
Or you can do something like this with bash:
```

#!/bin/bash

lynx -nonumbers -dump sports.espn.go.com/nfl/scoreboard |
egrep -i -A4 -B1 New\ York\ Jets |
{
    # Read the first two lines into $team1 and $team2
    read team1  
    read team2  
    # Read and forget the CBS and 1 2 3 4 lines
    read        
    read
    # Read the last two lines into $info1 and $info2
    read info1 
    read info2

    # And print
    printf "%-40s %s\n" "$team1" "$info1"
    printf "%-40s %s\n" "$team2" "$info2"
}

```

---

### Post by parm289 on 2008-11-30
[i]vor - Actually, the first script is more suitable for my Conky setup (but thanks for the second effort!).

One more thing - the table I'm reading from on the website is formatted differently if the team is home or away.  If the team is home, it is the second team listed; if it's away, it's the first team listed.  (Try substituting "Giants" for "Jets" in your first script)

I think I'll need an if, else loop to determine the home/away status and grep the correct lines...but, I don't know how to do this in perl...
[/i]
EDIT:  geirha - that works!  With that format I now have the teams, score, and last play.  I still need the script to determine if the team is home/away....

---

### Post by geirha on 2008-11-30
All the entries seem to have the 1 2 3 4 line, so if you match with that instead ...

One of the entries (Jacksonville vs Houston) doesn't have the CBS/NFL/FOX/etc. line, so that messes it up a bit, but you might be able to build on this to handle such cases as well.
```

#!/bin/bash

lynx -nonumbers -dump sports.espn.go.com/nfl/scoreboard |
egrep -B3 -A2 '1[[:space:]]+2[[:space:]]+3[[:space:]]+4' |
while true; do
    read team1
    read team2
    read
    read
    read info1
    read info2

    # If one of the teams matches "Giants" or "Jets"
    if [[ "$team1 $team2" =~ Giants|Jets ]]; then
        printf "%-40s %s\n" "$team1" "$info1"
        printf "%-40s %s\n" "$team2" "$info2"
    fi

    # Next line should be a seperator line --, or no line, in which case we
    # break out of the loop
    if ! read; then
        break;
    fi
done

```

---

### Post by parm289 on 2008-11-30
Thanks!  Now I have to figure out how to get my .conkyrc to look good...

---

