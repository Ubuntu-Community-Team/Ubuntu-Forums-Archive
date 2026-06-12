---
title: "Jaunty boots to a black screen with cursor"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by RobertWaelder on 2009-04-23
This was already posted [at this link]("http://ubuntuforums.org/showthread.php?t=1129192&highlight=jaunty+black+screen+after+login"). Since the Jaunty testing forum is closed now, I'd like to resurrect this post. So basically, after I input my name and password at the login screen, the screen goes black and I am left with a lonely little arrow (the cursor). It pretty much just stays there indefinitely. I can access a terminal via Ctrl + Alt + Fn, and everything in the console works fine. First I tried removing "nvidia-common" using apt-get as recommended in the previous thread, but when I rebooted, same deal. Then I booted using Failsafe mode in Gnome. This was a little more successful, as I actually got to see the wallpaper, but not soon after that I received two error messages. The first: "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)" and the next: "Nautilus could not create the following required folders: /home/robzilla/Desktop, /home/robzilla/.nautilus. Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them." Soooo.... if anyone could help me figure this issue out, I would be extremely grateful. I really wanna try out Jaunty!:popcorn:

Oh btw, misc information: I'm running 64-bit Ubuntu on an HP Pavilion dv9000, and I'm dual booting alongside Windows.

---

### Post by danlea on 2009-04-24
It could be the same issue I was having (and took me literally all day to figure out).  Is your ~/.pulse directory owned by root?  If so, delete it.

---

### Post by RobertWaelder on 2009-04-24
Hmm, I think I'll try just changing the permissions before I delete it, but I'll try that! Thanks.

---

### Post by RobertWaelder on 2009-04-24
Hmm, I did ls -a on /home/robzilla, but all I saw was .pulse-cookie (which was a blank text file). Wierd. I think I'll try uninstalling pulse audio altogether.

---

### Post by danlea on 2009-04-24
Well the bug is detailed at the link below, so if it's not applicable to you, there's no need to uninstall pulse audio.  I found it through the ~/.xsessions-errors line:
E: core-util.c: Failed to create secure directory: Permission denied

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/330766](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/330766)

---

### Post by RobertWaelder on 2009-04-24
I looked in /root and found a .pulse directory. When I moved it to my home directory, I was able to get a little bit further, and I actually heard the startup sound. It was a little jilted and wonky sounding though. Anyway, I got the same error messages as if I had logged in through the failsafe mode. I decided to check the log file that the first error message mentioned for any clues, and it was a bunch of garbled text with the occasional bit of readable text. I was told it "may be a binary file". I read the readable bits, and it mentioned something about problems with separately mounted /home directories (which I suspected anyway). I'll try to get that file copied to a USB drive so I can post it. Maybe someone will be able to make sense of it.

---

### Post by RobertWaelder on 2009-04-24
Here is the full log file created by the error message. It's rather confusing, so I'll post the full one, plus an abridged version with the important stuff in it.

[PHP]ELF          >     @     @       `2          @ 8 	 @         @       @ @     @ @     ø      ø                   8      8@     8@                                          @       @     |'      |'                    ¸-      ¸-`     ¸-`     ¨      È                    à-      à-`     à-`                                T      T@     T@                            Påtd   h&      h&@     h&@     4       4              Qåtd                                                  Råtd   ¸-      ¸-`     ¸-`     H      H             /lib64/ld-linux-x86-64.so.2          GNU                  %   :      '          6                     4            #      &       /   7   +   ,          (   9          3   1      *   )           $   %                               8                                               -                                  	      5   2                           
   .   "   !                      0          
                         -         &#8364; !	
&#710; @-   0   8   j	CÖºã&#8217;|CEÕì:&#8212;2bÛí¬KãÀfUaÚÍã&#382;ØqXj&#353;|¹ñâ&#382;ëÓï                                                                                         ú                     %                      è                     2                      H                       W                       Õ                     ð                     5                     Á                     &#8250;                     &#8224;                     ,                     o                     k                      &#8218;                      £                     &#8220;                      `                     &#376;                      i                     &                     S                     º                      =                     Ã                                           û                     ²                     Ó                      ë                      ü                                                                +                     8                     B                     {                     U                                                                ~    P1`             Z   ñÿ&#8364;1`             G   ñÿ`1`             &#8364;     P1`             &#8222;   
  @             o    @            &    `1`            &#8249;   
 @@     &#8240;       N   ñÿ`1`             B   
  @     +      «    P@             _   
 0@            i    @              libgtk-x11-2.0.so.0 g_free g_unlink g_slist_free g_option_context_free __gmon_start__ _Jv_RegisterClasses g_option_context_parse g_strdup_vprintf g_set_error g_option_context_add_group g_getenv g_file_open_tmp g_file_error_from_errno g_build_filename g_strerror g_option_context_new g_get_home_dir g_error_free g_mkstemp g_file_error_quark g_dgettext gtk_init_check gtk_dialog_add_buttons gtk_get_option_group gtk_message_dialog_new gtk_dialog_run gtk_dialog_get_type gtk_widget_destroy g_print g_printerr g_type_check_instance_cast libgconf-2.so.4 gconf_load_source_path gconf_resolve_address gconf_blow_away_locks gconf_ping_daemon gconf_source_free gconf_use_local_locks g_thread_init libgthread-2.0.so.0 libgobject-2.0.so.0 libglib-2.0.so.0 libpthread.so.0 close open __errno_location fcntl libc.so.6 stdin _IO_getc __libc_start_main _edata __bss_start _end __libc_csu_fini _IO_stdin_used __data_start __libc_csu_init GLIBC_2.2.5                                                                                                                  ui	   &#8250;        ê         ui	   &#8250;      à/`                   `1`        3            0`                   0`                   0`                   0`                    0`                   (0`                   00`                   80`        
           @0`                   H0`                   P0`        
           X0`                   `0`                   h0`                   p0`                   x0`                   &#8364;0`                   &#710;0`                   0`                   &#732;0`                   *0`                   ¨0`                   °0`                   ¸0`                   À0`                   È0`                   Ð0`                   Ø0`                   à0`                   è0`                    ð0`        !           ø0`        "            1`        #           1`        $           1`        %           1`        &            1`        '           (1`        (           01`        )           81`        *           @1`        +           H1`        ,           H&#402;ìèó  è&#8218;  èm  H&#402;ÄÃÿ5&#8218;  ÿ%&#8222;  @ ÿ%&#8218;  h    éàÿÿÿÿ%z  h   éÐÿÿÿÿ%r  h   éÀÿÿÿÿ%j  h   é°ÿÿÿÿ%b  h   é*ÿÿÿÿ%Z  h   éÿÿÿÿ%R  h   é&#8364;ÿÿÿÿ%J  h   épÿÿÿÿ%B  h   é`ÿÿÿÿ%:  h	   éPÿÿÿÿ%2  h
   é@ÿÿÿÿ%*  h   é0ÿÿÿÿ%"  h   é ÿÿÿÿ%  h
   éÿÿÿÿ%  h   é ÿÿÿÿ%
  h   éðþÿÿÿ%  h   éàþÿÿÿ%ú  h   éÐþÿÿÿ%ò  h   éÀþÿÿÿ%ê  h   é°þÿÿÿ%â  h   é*þÿÿÿ%Ú  h   éþÿÿÿ%Ò  h   é&#8364;þÿÿÿ%Ê  h   épþÿÿÿ%Â  h   é`þÿÿÿ%º  h   éPþÿÿÿ%²  h   é@þÿÿÿ%ª  h   é0þÿÿÿ%¢  h   é þÿÿÿ%&#353;  h   éþÿÿÿ%&#8217;  h   é þÿÿÿ%&#352;  h   éðýÿÿÿ%&#8218;  h    éàýÿÿÿ%z  h!   éÐýÿÿÿ%r  h"   éÀýÿÿÿ%j  h#   é°ýÿÿÿ%b  h$   é*ýÿÿÿ%Z  h%   éýÿÿÿ%R  h&   é&#8364;ýÿÿÿ%J  h'   épýÿÿÿ%B  h(   é`ýÿÿÿ%:  h)   éPýÿÿ        1íI&#8240;Ñ^H&#8240;âH&#402;äðPTIÇÀ0@ HÇÁ@@ HÇÇ @ è¿ýÿÿôH&#402;ìH&#8249;&#8240;  H&#8230;ÀtÿÐH&#402;ÄÃUH&#8240;åSH&#402;ì&#8364;=è   uK¸Ð-` H&#8249;â  H-È-` HÁøHXÿH9Ús%&#8364;    HBH&#8240;½  ÿÅÈ-` H&#8249;¯  H9ÚrâÆ&#8250;  H&#402;Ä[ÉÃfff.&#8222;     UH&#402;=ï   H&#8240;åt¸    H&#8230;Àt¿Ø-` I&#8240;ÃÉAÿã@ ÉÃUSHìØ   H&#8240;T$0¶ÐH&#8240;t$(H&#8226;    ºr@ H&#8240;L$8L&#8240;D$@L&#8240;L$HH&#8240;æH)ÂH&#8222;$Ï   ÿâ)xñ)pá)hÑ)`Á)X±)P¡)H&#8216;)@H&#8222;$ð   Ç$   ÇD$0   H&#8240;D$HD$ H&#8240;D$èÛüÿÿ&#8249;Ù  H&#8240;Å&#8230;Ò&#8222;&#8218;   &#8249;Ä  &#8230;ÀtXI&#8240;éA¸@ ¹   º   1ö1ÿ1ÀèRüÿÿH&#8240;ïH&#8240;Ãè§ûÿÿè2üÿÿH&#8240;ßH&#8240;ÆèGýÿÿH&#8240;ÇèOýÿÿH&#8240;ßèçûÿÿHÄØ   []ÃD  H&#8240;î¿§@ 1ÀèÙûÿÿHÄØ   []Ã&#8364;    1ö1ÿèoüÿÿÇ9     &#8240;/  é`ÿÿÿfH&#8240;\$ÐL&#8240;t$ðE1öL&#8240;|$øH&#8240;l$ØA&#8240;ÿL&#8240;d$àL&#8240;l$èH&#402;ìHèKüÿÿ&#8230;À»   t2L&#8240;÷èúúÿÿ&#8240;ØH&#8249;l$ H&#8249;\$L&#8249;d$(L&#8249;l$0L&#8249;t$8L&#8249;|$@H&#402;ÄHÃD  Ll$1Ò¾@ ¿$@ 1Àè&#732;üÿÿL&#8240;îH&#8240;ÇI&#8240;ÆHÇD$    èñûÿÿH&#8230;ÀI&#8240;ÄH&#8240;Ã&#8222;¢   f.&#8222;     H&#8249;+L&#8240;îHÇD$    H&#8240;ïèñûÿÿH&#8249;|$H&#8230;ÿu/H&#8240;Çè¯üÿÿH&#8249;;èWúÿÿH&#8249;[H&#8230;ÛuÆL&#8240;ç³ètúÿÿé=ÿÿÿ&#8364;    E&#8230;ÿD  t+H&#8249;_¾* @ ¿J@ è{üÿÿL&#8240;òH&#8240;ÇH&#8240;îH&#8240;Ù1ÀèýÿÿH&#8249;|$èüÿÿ1Ûéõþÿÿ&#8364;    E&#8230;ÿtJH&#8249;D$»ª@ H&#8240;ÝH&#8230;Àt¾1@ ¿J@ H&#8249;hè&üÿÿH&#8240;Ã¾Ø@ ¿J@ èüÿÿH&#8240;éH&#8240;ÇH&#8240;ÚL&#8240;ö1Àè)ýÿÿH&#8249;|$1ÛH&#8230;ÿu&#8217;é&#381;þÿÿ&#8222;     H&#8240;\$àL&#8240;d$èL&#8240;l$ðL&#8240;t$øH&#402;ìx&#8240;|$1ÿH&#8240;4$èaúÿÿ¾Q@ ¿J@ è²ûÿÿH&#8240;ÇèJûÿÿ1ÿH&#8240;ÃèðùÿÿH&#8240;ßH&#8240;ÆèeúÿÿHL$HHt$H&#8240;âH&#8240;ßHÇD$H    è÷ùÿÿH&#8240;ßè_ùÿÿH&#8249;T$HH&#8230;Òt]H&#8249;$L&#8249;b¾8!@ ¿J@ H&#8249;èKûÿÿL&#8240;æH&#8240;Ç1ÀH&#8240;ÚèKùÿÿH&#8249;|$Hèñúÿÿº   &#8240;ÐH&#8249;\$XL&#8249;d$`L&#8249;l$hL&#8249;t$pH&#402;ÄxÃf&#8222;     HÇD$@    è&#352;øÿÿ&#8230;À&#8222;Ú   ¿k@ HÇD$8    èïùÿÿH&#8230;À&#8222;>  ¿k@ èÜùÿÿ1ÒH&#8240;Ç¾*!@ 1Àè;úÿÿH&#8240;ÇH&#8240;D$@è~úÿÿ&#402;øÿA&#8240;Æ&#8222;*  L&#8249;d$8M&#8230;ä&#8222;À   èÏùÿÿL&#8249;l$@&#8249;¾à!@ M&#8249;d$¿J@ ètúÿÿL&#8240;îH&#8240;Ç&#8240;ÙL&#8240;â1ÀE1íè&#8225;ûÿÿH&#8249;|$8èúÿÿD&#8240;÷è
øÿÿH&#8249;|$@èó÷ÿÿ&#8230;À&#710;c  H&#8249;|$@èÑ÷ÿÿE&#8230;í&#8230;Ø   º   éòþÿÿfD  èÃùÿÿ1ÒH&#8240;Ç¾x@ 1Àè&#8218;ùÿÿH&#8240;ÇH&#8240;D$@è¥÷ÿÿH&#8249;|$@1ÀºÀ  ¾A   èÿùÿÿ&#8230;ÀA&#8240;Æ&#710;Ü  HT$1À¾   D&#8240;÷fÇD$ HÇD$    fÇD$  HÇD$     A½   èªùÿÿ&#8230;À&#8240;=ÿÿÿèÍøÿÿ&#8249;&#8240;ßèùÿÿL&#8249;l$@I&#8240;Ä¾ #@ ¿J@ èmùÿÿL&#8240;îH&#8240;Ç&#8240;ÙL&#8240;â1ÀE1íè&#8364;úÿÿéþþÿÿ 1ÿè±ûÿÿ1Ò&#8230;ÀD  &#8230;þÿÿ¾È$@ ¿J@ è+ùÿÿ&#8249;5¹  H&#8240;Ã&#8230;ö&#8222;'  &#8249;
¤  &#8230;É&#8222;Ø  I&#8240;Ù1ÉA¸@ º   1ö1ÿ1Àè1÷ÿÿ¾«@ ¿J@ I&#8240;Äèßøÿÿ¾µ@ ¿J@ I&#8240;ÆèÍøÿÿI&#8240;ÅèõöÿÿL&#8240;çH&#8240;ÆH&#8240;ÃèøÿÿE1ÉA¸ýÿÿÿL&#8240;ñºþÿÿÿH&#8240;ÇL&#8240;î1Àè	÷ÿÿH&#8240;ÞL&#8240;çèÞ÷ÿÿH&#8240;Çèæ÷ÿÿL&#8240;ç&#8240;Ãè|öÿÿ&#402;ûý&#8230;Kþÿÿ1Ò¾@ ¿$@ 1Àèà÷ÿÿ1öH&#8240;ÃH&#8240;ÇèC÷ÿÿH&#8240;ßI&#8240;ÄèèõÿÿM&#8230;äL&#8240;ã&#8222;n  @ H&#8249;;è0÷ÿÿH&#8249;;èÈõÿÿH&#8249;[H&#8230;ÛuçL&#8240;çèçõÿÿ¿   èuúÿÿ1Ò&#8230;À&#8221;ÂéÕüÿÿf&#8222;     è3÷ÿÿ&#8249;&#8240;ßèz÷ÿÿL&#8249;l$@I&#8240;Ä¾à!@ éaþÿÿè÷ÿÿ&#8249;8è\÷ÿÿL&#8249;d$@H&#8240;Ã¾&#8216;@ ¿J@ èµ÷ÿÿH&#8240;ÚH&#8240;ÇL&#8240;æ1Àèµõÿÿéeýÿÿ&#8222;     HT$8Ht$@¿*!@ è´öÿÿA&#8240;ÆéÚüÿÿ@ è³öÿÿ&#8249;&#8240;ßèúöÿÿL&#8249;l$@&#8240;ßI&#8240;ÄèËöÿÿ&#8240;Ãè4÷ÿÿH|$8&#8240;ÆM&#8240;áM&#8240;è¹À!@ &#8240;Ú1Àèéõÿÿé&#8217;üÿÿ¾¾@ ¿J@ è%÷ÿÿH&#8240;ÞH&#8240;Ç1ÀèøôÿÿH&#8249;=&#8240;  èlõÿÿ&#402;øY&#8222;þÿÿ&#402;øy&#8230;Òüÿÿfé&#8364;þÿÿ1ö1ÿ&#8364;    è£õÿÿÇm     &#8240;c  é´ýÿÿ¿8&@ 1ÀèÒôÿÿé&#382;þÿÿóÃfffff.&#8222;     H&#8240;l$ØL&#8240;|$øH-c  L=\  L&#8240;d$àL&#8240;l$èL&#8240;t$ðH&#8240;\$ÐH&#402;ì8L)ýA&#8240;þI&#8240;õHÁýI&#8240;ÔèËóÿÿH&#8230;ít1Û@ L&#8240;âL&#8240;îD&#8240;÷AÿßH&#402;ÃH9ërêH&#8249;\$H&#8249;l$L&#8249;d$L&#8249;l$ L&#8249;t$(L&#8249;|$0H&#402;Ä8ÃUH&#8240;åSH&#402;ìH&#8249;Ø  H&#402;øÿt»¸-` D  H&#402;ëÿÐH&#8249;H&#402;øÿuñH&#402;Ä[ÉÃH&#402;ìè_öÿÿH&#402;ÄÃ    %s path /etc/gconf/2 Error reading the file:  GConf2 - Sanity checks for GConf GCONF_TMPDIR .gconf-test-locking-file Can't remove file %s: %s
 _Continue _Log Out %s Continue (y/n)?        Please contact your system administrator to resolve the following problem:
No configuration sources in the configuration file "%s"; this means that preferences and other settings can't be saved. %s%s Please contact your system administrator to resolve the following problem:
Could not resolve the address "%s" in the configuration file "%s": %s        Error while parsing options: %s.
Run '%s --help' to see a full list of available command line options.
 gconf-test-locking-file-XXXXXX  Failed to create file '%s': %s  Please contact your system administrator to resolve the following problem:
Could not open or create the file "%s"; this indicates that there may be a problem with your configuration, as many programs will need to create files in your home directory. The error was "%s" (errno = %d).      Please contact your system administrator to resolve the following problem:
Could not lock the file "%s"; this indicates that there may be a problem with your operating system configuration. If you have an NFS-mounted home directory, either the client or the server may be set up incorrectly. See the rpc.statd and rpc.lockd documentation. A common cause of this error is that the "nfslock" service has been disabled.The error was "%s" (errno = %d).        The files that contain your preference settings are currently in use.

You might be logged in to a session from another computer, and the other login session is using your preference settings files.

You can continue to use the current session, but this might cause temporary problems with the preference settings in the other session.

Do you want to continue?       Failed to load addresses to delete locks
       ;4      ¨ïÿÿP   èðÿÿp   &#732;òÿÿ&#732;   È÷ÿÿÐ   Ø÷ÿÿè              zR x        @ >   AAGð&#402;&#8224; $   <   P@ ¨   J&#381;&#402;M&#8224;QP&#338;         d    @ +   X&#8364;&#381;&#338;&#402;          zR x        ðöÿÿ           $   4   èöÿÿ&#8240;    J&#8224;f@&#402;&#381;&#338;                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       ÿÿÿÿÿÿÿÿ        ÿÿÿÿÿÿÿÿ                                                  ±             Å             Ù             ê                          P@     
       @            x@     õþÿo     @            Ð	@            `@     
       §                                          è/`            ð                           `@            0@            0       	              þÿÿo    ð
@     ÿÿÿo           ðÿÿo    x
@                                                                                                             à-`                     ~@     &#381;@     &#382;@     ®@     ¾@     Î@     Þ@     î@     þ@     @     @     .@     >@     N@     ^@     n@     ~@     &#381;@     &#382;@     ®@     ¾@     Î@     Þ@     î@     þ@     @     @     .@     >@     N@     ^@     n@     ~@     &#381;@     &#382;@     ®@     ¾@     Î@     Þ@     î@     þ@     @                     gconf-sanity-check-2    Íy .shstrtab .interp .note.ABI-tag .gnu.hash .dynsym .dynstr .gnu.version .gnu.version_r .rela.dyn .rela.plt .init .text .fini .rodata .eh_frame_hdr .eh_frame .ctors .dtors .jcr .dynamic .got .got.plt .data .bss .gnu_debuglink                                                                                 8@     8                                                 T@     T                                     %             x@     x      &#8222;                           !   öÿÿo        @            `                             +             `@     `      p                          3             Ð	@     Ð	      §                             ;   ÿÿÿo       x
@     x
      t                            H   þÿÿo       ð
@     ð
      @                            W             0@     0      0                            a             `@     `      ð                          k             P@     P                                    f             h@     h      °                            q              @            è	                             w             @                                         }             @           P                             &#8230;             h&@     h&      4                              &#8220;             *&@     *&      Ü                                           ¸-`     ¸-                                    ¤             È-`     È-                                    «             Ø-`     Ø-                                    °             à-`     à-                                  ¹             à/`     à/                                   ¾             è/`     è/      h                            Ç             P1`     P1                                    Í             `1`     `1                                     Ò                      `1                                                          |1      á                              [/PHP]

[PHP]%s path /etc/gconf/2 Error reading the file:  GConf2 - Sanity checks for GConf GCONF_TMPDIR .gconf-test-locking-file Can't remove file %s: %s
 _Continue _Log Out %s Continue (y/n)?        Please contact your system administrator to resolve the following problem:
No configuration sources in the configuration file "%s"; this means that preferences and other settings can't be saved. %s%s Please contact your system administrator to resolve the following problem:
Could not resolve the address "%s" in the configuration file "%s": %s        Error while parsing options: %s.
Run '%s --help' to see a full list of available command line options.
 gconf-test-locking-file-XXXXXX  Failed to create file '%s': %s  Please contact your system administrator to resolve the following problem:
Could not open or create the file "%s"; this indicates that there may be a problem with your configuration, as many programs will need to create files in your home directory. The error was "%s" (errno = %d).      Please contact your system administrator to resolve the following problem:
Could not lock the file "%s"; this indicates that there may be a problem with your operating system configuration. If you have an NFS-mounted home directory, either the client or the server may be set up incorrectly. See the rpc.statd and rpc.lockd documentation. A common cause of this error is that the "nfslock" service has been disabled.The error was "%s" (errno = %d).        The files that contain your preference settings are currently in use.

You might be logged in to a session from another computer, and the other login session is using your preference settings files.

You can continue to use the current session, but this might cause temporary problems with the preference settings in the other session.

Do you want to continue?       Failed to load addresses to delete locks[/PHP]

I'm going to try completely uninstalling pulseaudio via apt-get. Couldn't hurt, right?

EDIT: Completely removing pulse-audio had no effect.

---

### Post by p310don on 2009-04-25
I had the issue when upgrading from 8.10 to  9.04 where I left the computer to do its thing for an hour or so, and when I came back, I had a black screen with a cursor, nothing else. I reset the machine, got a login which looked normal, so did the usual, however it came back to the black screen with mouse cursor and nothing at all. After much searching and mucking around, I discovered a solution. Apparently the upgrade didn't finish. To do so, open terminal, ie ctrl alt f2 and type

[B]sudo dpkg --configure -a

Let it continue the upgrade, which took about ten to fifteen mins, then when all is done, type

sudo reboot

And then login. This got me to the gnome desktop, where the notification icon told me a I had a bunch of updates. After installing all updates, I'm now enjoying 9.04.

Hope this helps other users who are also losing hair from frustration. :)
[/B]

---

### Post by RobertWaelder on 2009-04-25
So simple it just might work!

---

### Post by RobertWaelder on 2009-04-25
That didn't work either :-( I am sad now.

---

### Post by pavel__ on 2009-04-26
[http://ubuntuforums.org/showthread.php?t=1135402](http://ubuntuforums.org/showthread.php?t=1135402)

same thing, but already by using livecd, without installing at all.

---

### Post by RobertWaelder on 2009-04-29
So I figured it out. I am now the proud user of a shiny new Jaunty installation, w00t. :) Basically, I failed to realize when I imported all my Windows settings that I had filled up the /home partition to capacity and nautilus and some configuration programs couldn't create the files they needed to start up. When I did 'df' at the terminal I saw my drive was full and had an aha moment haha. I simply deleted some of the data from the hard drive and voila! Working installation. Thanks everyone for your help and advice!

---

### Post by Snif on 2009-06-16
Had the same error after upgrading from 8.10, alongwith "users $HOME/.dmcr file is being ignored....user's $HOME directory must be owned by user and not writeable to other users" ( [http://ubuntuforums.org/showthread.php?t=1062651]("http://ubuntuforums.org/showthread.php?t=1062651") ) problem.
Black screen with cursor fixed with
```
sudo chown -R user:user /home/user
sudo chmod -R 744 /home/user/
sudo chmod 777 /home/user/.dmcr
```

BTW, I had no .dmcr file in my home directory, so I created it as user.

It may be something wrong with those commands, but they fix the problem. 
Please correct me if there's something wrong!

Regards, Michael.

---

### Post by mhgsys on 2009-06-16
> **Snif said:**
> H
It may be something wrong with those commands, but they fix the problem. 
Please correct me if there's something wrong!

Regards, Michael.

I've seen that error get fixed with these commands;

```

sudo chmod 644 /home/username/.dmrc

```
```

sudo chown username /home/username/.dmrc

```
```

sudo chmod 755 /home/username

```

---

