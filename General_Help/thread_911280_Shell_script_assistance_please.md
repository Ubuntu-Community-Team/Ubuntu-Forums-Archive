---
title: "Shell script assistance please?"
date: 2008-09-05
forum: General Help
---

### Post by the_nite_owl on 2008-09-05
I am not terribly familiar with shell scripting yet.
Can someone assist me with this script?

opscmd job_list | \
grep 'INTERRUPTED' | \
while read str; do
  jobnumber="$( echo "$str" | sed 's/.*\(.........\)$/\1/' )"
  opscmd job_get "$jobnumber" dest_id | \
  grep -q 'FXQTRLY' &&
  opscmd job_hold "$jobnumber"
done

This script is executing the command "opscmd job_list" then checking each line of text returned for the text INTERRUPTED and if found it takes the job number from the end of that line and issues the command "opscmd job_get jobnumber dest_id" then checks that line to see if it has the text FXQTRLY.  If the text is found then it will issue the command "opscmd job_hold jobnumber".


What I want to do is, if the tests all evaluate true and it is going to issue the job_hold command, I want to take the original line stored in str and write it out to a text file.
At this point it would probably be best if it appended the line to an existing text file but the text of str preceded by the date/time it was written.
I suspect it is not a difficult thing to accomplish but I have no experience selectively writing to an external file and am not quite sure how the command would fit into the script so that it only executed under the conditions that would issue the job_hold command.

Any help would be appreciated.

---

### Post by HermanAB on 2008-09-05
You can echo, cat or pipe stuff to a file:
echo $1 > filename

Some googling will yield many Bash guides online, but nothing beats a book or two.  I use Classic Shell Scripting by Robbins and Beebe.

Cheers,

Herman

---

### Post by the_nite_owl on 2008-09-05
> **HermanAB said:**
> You can echo, cat or pipe stuff to a file:
echo $1 > filename

Some googling will yield many Bash guides online, but nothing beats a book or two.  I use Classic Shell Scripting by Robbins and Beebe.

Cheers,

Herman

With a little testing I came up with this:

opscmd job_list | \
grep 'READY' | \
while read str; do
  jobnumber="$( echo "$str" | sed 's/.*\(.........\)$/\1/' )"
  opscmd job_get "$jobnumber" dest_id | \
  grep 'FXQTRLY' &&
  opscmd job_hold "$jobnumber" &&
  echo "$str" >> /ops/fixscripts/interrupted.log
done

Was easier than I thought it would be.  I had to drop the -q from the grep line of the original script as it gave me errors but it seems to work well now.
Is this the correct use of the && to chain multiple commands to the successful match of the FXQTRLY text?

The one additonal thing I could want is to have a date or date/time stamp for each line that is entered so we can tell when each action was performed.  Necessary since the file is appended to and not a new file generated for each run of the script.  We need it for future audit purposes.

Thanks.

---

