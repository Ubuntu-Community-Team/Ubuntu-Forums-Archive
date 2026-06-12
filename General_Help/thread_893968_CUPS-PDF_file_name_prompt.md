---
title: "CUPS-PDF file name prompt"
date: 2008-08-18
forum: General Help
---

### Post by kaibob on 2008-08-18
Over the past few months, a number of forum members have requested help in configuring cups-pdf to prompt for a file name. With the help of the threads credited below, I got this working and thought I would pass along the procedure I followed.

1) Create a script similar to the sample script below and place it in a folder in your path (~/bin is good). 

2) Open the file /etc/apparmor.d/usr.sbin.cupsd in a text editor and add the path to the script at the end of this file just before the final } symbol. After the path append uxr,. An example is:

> /home/kaibob/bin/cupscript.sh uxr,

3) Open the file /etc/cups/cups-pdf.conf in a text editor, remove the # symbol before the line that begins with postprocesssing, and add the path to the script after postprocessing. An example is:

> PostProcessing /home/kaibob/bin/cupscript.sh 

4) Restart apparmor (ignore warning messages):

> sudo /etc/init.d/apparmor restart 

5) Restart your computer (seems to be necessary).

The sample script contained below works but is intentionally barebones--you will want to gussy it up a bit to fit your needs. It uses zenity, which I believe is installed by default in Hardy, but is otherwise available in the repo's. Be sure to back up all files before editing them. 

SAMPLE SCRIPT 
> #!/bin/bash
CURRENT_PDF="${1}"
CURRENT_USER="${2}"
DISPLAY=:0.0
export DISPLAY
XAUTHORITY=/home/${CURRENT_USER}/.Xauthority
export XAUTHORITY
PDFNAME=$(zenity --file-selection --save --confirm-overwrite)
mv "$CURRENT_PDF" "$PDFNAME"

SOURCES - CREDIT
[http://ubuntuforums.org/showthread.php?t=750426](http://ubuntuforums.org/showthread.php?t=750426)
[http://ubuntuforums.org/showthread.php?t=837257](http://ubuntuforums.org/showthread.php?t=837257)

---

### Post by mmullis on 2009-09-23
I've not been able to get this working.  If I execute postpdf.sh <filename> from the shell I get the new dialog box and the send to email button works as expected. However when printing to the cups-pdf printer I get the new dialog box, but the send to email button does not launch Evolution. No error is generated. 

I'm not sure how to troubleshoot this further.

---

### Post by mmullis on 2009-09-23
Update. I've had limited success using a modified version of the script posted eariler.

```

#!/bin/bash
CURRENT_PDF="${1}"
CURRENT_USER="${2}"
DISPLAY=:0.0
export DISPLAY
XAUTHORITY=/home/${CURRENT_USER}/.Xauthority
export XAUTHORITY
PDFNAME=$(evolution mailto:?attach=$CURRENT_PDF)
mv "$CURRENT_PDF" "$PDFNAME"

```This will launch Evolution with the file attached. The problem I encounter with this is after the email is sent an evolution process is left running in the background. Subsequent cups-pdf print jobs will not launch Evolution until the background process is killed. I'm just doing a quick and diry killall -9 evolution.

I would actually prefer to do this with Thunderbird but mozilla-thunderbird does not launch when I use it in the script. It will however if I run the script from the shell.

---

### Post by kaibob on 2009-09-23
I'm glad to hear you got this working. If I understand correctly, the basic process described in my original post still works. 

I looked at your script, and I don't understand the last two lines. I know absolutely nothing about email clients, but why use command substitution with evolution to send the PDF as an attachment and then afterwards rename the PDF based on that command substitution. Is the PDF actually being renamed? I guess if it works that's all that matters.

---

### Post by mmullis on 2009-09-23
> **kaibob said:**
> I'm glad to hear you got this working. If I understand correctly, the basic process described in my original post still works. 

I looked at your script, and I don't understand the last two lines. I know absolutely nothing about email clients, but why use command substitution with evolution to send the PDF as an attachment and then afterwards rename the PDF based on that command substitution. Is the PDF actually being renamed? I guess if it works that's all that matters.


I should remove the last line. The second to last line just fires up Evolution's composer with the pdf already attached. It has now mysteriously started working properly without having to kill any processes in between sends.

I just needed a way to email .pdf invoices from GNUCash. This works much better than saving the .pdf, running Evolution and browsing for the pdf to attach.

It would be nice to see this feature added permanantly to cups-pdf since this functionality is already present in kprinter for KDE users.

Thanks again

---

### Post by essin on 2011-07-28
Nice procedure except it does not include making the script executable 
chmod +x cupscript.sh

---

### Post by vinodhkumarsampath on 2011-10-31
Working fine, but the default location goes to my root directory, can it be changed to any particular directory in my home dir..?
vinodh kumar sampath:KS

---

### Post by Matsumoto on 2012-01-15
Thanks, I just took the code and made three simple improvements.
1.) First I set some title and a different default file name
2.) If you click cancel the file is not moved
3.) Prepend the current date to the suggested file name

Have fun!

```
#!/bin/bash
CURRENT_PDF="${1}"
CURRENT_USER="${2}"
DISPLAY=:0.0
export DISPLAY
XAUTHORITY=/home/${CURRENT_USER}/.Xauthority
export XAUTHORITY


# Prepend date for current filename suggestion
SUGGEST_PDF="${CURRENT_PDF%/*}/$(date -I)_${CURRENT_PDF##*/}"
# Use this instead for keeping the file name
# SUGGEST_PDF="${CURRENT_PDF}"

# Ask for it
PDFNAME=$(zenity --file-selection \
                 --title="CUPS: Select PDF print file name" \
                 --filename ${SUGGEST_PDF} --save --confirm-overwrite)

# Move it, when not canceled
if [ ! -z "${PDFNAME}" ]; then
   mv "$CURRENT_PDF" "$PDFNAME"
fi

```

---

