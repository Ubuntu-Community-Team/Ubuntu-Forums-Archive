---
title: "Post regarding installation of Mesa-7.5"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by Absu Gehennah on 2009-09-01
Hello to all :)
I'm having problems with installing Mesa-7.5 which I need badly...I followed the process explained on this post [http://ubuntuforums.org/showpost.php?p=2960650&postcount=3](http://ubuntuforums.org/showpost.php?p=2960650&postcount=3)
And i stuck where it says that I need in terminal use this command $ tar xzvf MesaLib-7.0.tar.gz

And then terminal shows me this 
absu@Divine-Intervention:~$ tar xzvf MesaLib-7.0.tar.gz
tar: MesaLib-7.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

How come terminal cannot find that file since i extracted it and saved it?
Maybe there is some special place where I needed to save it?
Thx in advance for the time :)

---

### Post by mc4man on 2009-09-01
Just to point out a few things from your post, though i may suggest you might want to seek a solution/advice to the reason for this before following a 2 year old post (though it still may be valid, also considering your getting hung up already

> which I need badly..

Any way 
this command, at that directory prompt, will extract the files from  MesaLib-7.0.tar.gz and only if MesaLib-7.0.tar.gz  was loose in your home folder

> absu@Divine-Intervention:~$ tar xzvf MesaLib-7.0.tar.gz

This seems to indicate your archive would be named MesaLib-7.5.tar.gz
> 
with installing Mesa-7.5 

And this seems to indicate you've already extracted the files (folder)

> How come terminal cannot find that file since i extracted it and saved it?

Though maybe by saying "extracted it and saved it" you mean downloaded the ,,tar.gz?

If you wish to proceed you want to clear this up a bit

---

### Post by Absu Gehennah on 2009-09-01
Well this 2 year old post is my lead clue for installing.Since installing messa is part of bigger puzzle of what I actually need to do.The thing is that in post it says that I'm installing Mesa 7.0 but at that download link it redirects me to Mesa 7.5.I suppose there is not much difference in procedure besides changing that key word from 7.0 to 7.5.
Well I did as you said (extracted ..tar.gz to home folder) then I continued to follow steps of installation but then I hit blockade again.After i entered 
    $ cd Mesa-7.5 and tryed to start compiling for my 32-bits platform Terminal showed me this"

absu@Divine-Intervention:~/Mesa-7.5$ make linux-dri-x86
(cd configs && rm -f current && ln -s linux-dri-x86 current)
make default
make[1]: Entering directory `/home/absu/Mesa-7.5'
make[2]: Entering directory `/home/absu/Mesa-7.5/src'
Making sources for linux-dri-x86
make[3]: Entering directory `/home/absu/Mesa-7.5/src/glx/x11'
rm -f depend
touch depend
makedepend -fdepend -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi -I/usr/include/drm    -I/usr/X11R6/include glcontextmodes.c clientattrib.c compsize.c eval.c glxcmds.c glxcurrent.c glxext.c glxextensions.c indirect.c indirect_init.c indirect_size.c indirect_window_pos.c indirect_texture_compression.c indirect_transpose_matrix.c indirect_vertex_array.c indirect_vertex_program.c pixel.c pixelstore.c render2.c renderpix.c single2.c singlepix.c vertarr.c xfont.c glx_pbuffer.c glx_query.c drisw_glx.c dri_common.c dri_glx.c XF86dri.c glxhash.c dri2_glx.c dri2.c \
        ../../../src/mesa/main/dispatch.c ../../../src/mesa/glapi/glapi.c ../../../src/mesa/glapi/glapi_getproc.c ../../../src/mesa/glapi/glthread.c ../../../src/mesa/x86/glapi_x86.S 
make[3]: makedepend: Command not found
make[3]: *** No rule to make target `depend', needed by `default'.  Stop.
make[3]: Leaving directory `/home/absu/Mesa-7.5/src/glx/x11'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/absu/Mesa-7.5/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/absu/Mesa-7.5'
make: *** [linux-dri-x86] Error 2
absu@Divine-Intervention:~/Mesa-7.5$ 

And that's it.If u can see from this what did I do wrong please tell me.

After alot og googling I found out that Mesa 7.5 isn't supporting radeon x400 series of graphic cards.Guess lock would be fine.

---

