---
title: "Making a terminal shell using C?"
date: 2008-11-16
forum: General Help
---

### Post by supershin on 2008-11-16
Hi, I have an assignment which requires me to take user input, such as, ls -l | wc -l or  ls -l | wc -l > out.txt 
create a child process, using fork, to execute the commands, using execv, and display the output to screen or to where ever the output redirection operator specify.

I have read a book, read some articles on the net and even in forums, also tried writing some code to get ls -l | wc -l  to work but it doesn't. I can get just ls -l to work.

Here is what I'm trying to do.
A method makeChild will do the pipe, fork and exec. The parent will wait till the child completes. I don't know what the order of executing the processes are. 
I suppose I need a loop which moves through an array, arr, containing the args ls -l in index 0 and wc -l in index 1. 
Do I let the 1st child execv ls -l then pass its output to the next child? or do I let the 1st child, make another child till end of array, arr, reached and let the last child call ls -l and the 2nd last child call wc -l and let each parent read from the child?

Also, where do the output redirection fit in? 

*sigh* I'm soo confused. Any help will greatly appreciated. 
Links to detailed tutorials/posts/sample code or any related material welcomed, even IRC addresses for discussions.

---

