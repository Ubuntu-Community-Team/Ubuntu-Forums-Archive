---
title: "Sketchup and ruby scripts"
date: 2008-10-23
forum: General Help
---

### Post by nikkkko on 2008-10-23
I just figured out how to get Ruby scripts to work under SU and seeing as searching here on the words Ruby and Sketchup only brought up 3 replies, I thought I'd post my solution. 

If you are running SU under Wine and can't get ruby scripts to work, it's apparently because the files were originally written with a windows text editor with a different character encoding.  When you run SU you get a syntax error instead of, say, a nice bezier curve tool.

The remedy I use is simple.  Open the script in OpenOffice and accept the dialogue box to use Unicode ( UTF-8 ), then select all the text and copy it into an empty Gedit file.  Save that file under it's original name in the SU plugins directory, (or wherever you are meant to for that script), and the file should now have the correct encoding.

Hope that helps someone out there.

---

