---
title: "Perform this operation on ~50 files?"
date: 2008-09-15
forum: General Help
---

### Post by ThinkBuntu on 2008-09-15
I'm working in CygWin on my office Windows box to speed up development, and I need to do the following to finish up some work:

[LIST]
[*]Wrap the first line in <h1> tags
[*]Add some text at the beginning of each file
[*]Add some text to the end of each file
[/LIST]

How would you go about this using any combination of Bash scripting, Sed, Awk, and Vim? The files share a common extension, and I've had no problem performing a regex (wrap record rows as table rows) and batch rename over the files, and this is the last step.

---

### Post by dayanandasaraswati on 2008-09-15
Can you be more specific..You want to wrap first lines with h1 tags and where do you wanna add few lines. Do you want to add the same text to all files and do you want to add these lines after the first line or before the first line. To what kind of files these additions are to be carried out. Are they simple notepad/text files or are they rich text formatted files like rtf, doc, docx. If they are of first type then we can surely write a C program that can do this job.

---

### Post by ThinkBuntu on 2008-09-15
> **dayanandasaraswati said:**
> Can you be more specific..You want to wrap first lines with h1 tags and where do you wanna add few lines. Do you want to add the same text to all files and do you want to add these lines after the first line or before the first line. To what kind of files these additions are to be carried out. Are they simple notepad/text files or are they rich text formatted files like rtf, doc, docx. If they are of first type then we can surely write a C program that can do this job.

Plain text (.cfm), and I don't think that a C program will be the best answer here. I'm looking for a solution to perform this fairly simple task using Unix command line tools. I might do this with vi, but I don't have an easy way to open all relevant files with GVim and CygWin working separately.

I'm not sure if I can make the other requirements any clearer. The first line (with text on it) should be wrapped in <h1> tags. Then, a few lines of text need to be added at the beginning and end of the file.

---

