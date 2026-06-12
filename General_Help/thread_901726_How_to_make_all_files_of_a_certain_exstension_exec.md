---
title: "How to make all files of a certain exstension executables"
date: 2008-08-26
forum: General Help
---

### Post by maxbaroi on 2008-08-26
While following [these]("http://ubuntuforums.org/archive/index.php/t-356350.html") instructions someone remarks "Don't forget to make all the .rbx (or .rb) files executable."

How exactly would you go about doing that?

---

### Post by mb_webguy on 2008-08-26
Open the terminal and change to the directory containing the .rb or .rbx files, then type "sudo chmod a+x ./*.rb*".

---

### Post by maxbaroi on 2008-08-26
Thank you, and how would I do that recursively among a directory and all its subdirectories?

---

### Post by mb_webguy on 2008-08-26
To make all .rbx files everywhere executable, use the commmand "sudo find / -name *.rbx -exec chmod a+x '{}' \;".  To do the same for all .rb files, re-enter the command using "*.rb" in place of "*.rbx".

Be *very* careful with this, however.  The combination of "sudo"  and the exec option of the find command is extremely powerful.  Don't try the "*.rb*" syntax from the previous command to modify all .rb and .rbx files, since this would change the file permissions of any file with ".rb" in the filename anywhere on your system.  Never run a find command with the exec option, especially using sudo, unless you're *absolutely sure* what the command will do, and *exactly* which files will be affected.

If you only want all .rb and .rbx files in a particular directory tree modified, then use that directory in the find command instead of the root directory, for example "sudo find /my/path/to/files -name *.rbx -exec chmod a+x '{}' \;"  This is a bit less risky.  If you have write permissions for all files in the directory tree, you can leave off sudo.

Actually, it wouldn't be a bad idea to run "sudo find / -name *.rbx" and "sudo find / -name *.rb" before running the commands with the exec option to see the files you'll be modifying.

Also, this will only make any .rb and .rbx files currently on your system executable.  This will not affect the permissions of any files you create or download at a later point.

---

### Post by mssever on 2008-08-26
> **maxbaroi said:**
> While following [these]("http://ubuntuforums.org/archive/index.php/t-356350.html") instructions someone remarks "Don't forget to make all the .rbx (or .rb) files executable."
That's not necessary. You only need to make the main scripts executable, not individual libraries.

---

