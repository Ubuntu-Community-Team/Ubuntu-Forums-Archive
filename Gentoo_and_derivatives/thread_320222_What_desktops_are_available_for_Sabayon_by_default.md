---
title: "What desktops are available for Sabayon by default upon install and boot?"
date: 2006-12-16
forum: Gentoo and derivatives
---

### Post by RAV TUX on 2006-12-16
5 desktops environments:

upon install:

1. KDE
2. Gnome
3. XFCE
4. Enlightenment 16
5. Fluxbox

I booted into the Sabayon Live DVD and entered into the installer to capture a screenshot of the desktop environments available....

now no matter which one you load they all are available for your choice upon boot into your installed Sabayon....at the sign in screen....
  
upon sign in:

1. default
2. custom
3. E16
4. Fluxbox
5. Gnome
6. KDE 3.5
7. XFCE
8. Failsafe

I am sure you could emerge more...

---

### Post by RAV TUX on 2006-12-16
Sabayon Gnome (default no customization)

[[IMG]http://img431.imageshack.us/img431/5317/screenshotca5.th.png[/IMG]](http://img431.imageshack.us/my.php?image=screenshotca5.png)

---

### Post by codejunkie on 2006-12-16
> **RAV TUX said:**
> 5 desktops environments:

1. KDE
2. Gnome
3. XFCE
4. Enlightenment 16
5. Fluxbox

I booted into the Sabayon Live DVD and entered into the installer to capture a screenshot of the desktop environments available....

now no matter which one you load they all are available for your choice upon boot into your installed Sabayon....at the sign in screen....

I am sure you could emerge more...

I've got some questions for you, i seen you post several reviews about different distros Sabayon mostly so how does Sabayon compare to Gentoo, does it take hours to install and compile everything or is the base system precompiled and you only suffer through the compile time on newly installed applications and if it is precompiled is there much of a performance loss compared to Gentoo.

---

### Post by yabbadabbadont on 2006-12-16
You were going to post screenshots of the default desktop using each of the others weren't you?  :D

Please start with Fluxbox.

---

### Post by RAV TUX on 2006-12-16
Sabayon XFCE

(btw another nice thing to change desktop environments does NOT require a reboot...you simple logout and it takes you back to Sabayon signin screen where you select your desktop session...)

---

### Post by RAV TUX on 2006-12-16
> **codejunkie said:**
> I've got some questions for you, i seen you post several reviews about different distros Sabayon mostly so how does Sabayon compare to Gentoo, does it take hours to install and compile everything or is the base system precompiled and you only suffer through the compile time on newly installed applications and if it is precompiled is there much of a performance loss compared to Gentoo.

About 15 minutes to install it comes precompiled....on newly installed programs takes a few minutes just by using emerge...

no performance loss compared to Gentoo....Sabayon is still Gentoo

---

### Post by yabbadabbadont on 2006-12-16
> **RAV TUX said:**
> About 15 minutes to install it comes precompiled....on newly installed programs takes a few minutes just by using emerge...

no performance loss compared to Gentoo....Sabayon is still Gentoo

Sure, but I bet it's installer doesn't randomly destroy your partition table.  Where's the fun in that?  At least the GLI appeals to the gambler in people.  :twisted:

---

### Post by RAV TUX on 2006-12-16
> **yabbadabbadont said:**
> You were going to post screenshots of the default desktop using each of the others weren't you?  :D

Please start with Fluxbox.

my apologies for not starting with Fluxbox....but I have to say Fluxbox is noticably faster to me then KDE, Gnome, and XFCE....

I actually like Fluxbox alot....

I may use this for a while after a finish my screenshot tour from each desktop environment
[[IMG]http://img267.imageshack.us/img267/8868/sabayonfluxboxqx6.th.png[/IMG]](http://img267.imageshack.us/my.php?image=sabayonfluxboxqx6.png)

---

### Post by scxtt on 2006-12-17
> **yabbadabbadont said:**
> Sure, but I bet it's installer doesn't randomly destroy your partition table.  Where's the fun in that?  At least the GLI appeals to the gambler in people.  :twisted:good, i'm not the only one that happened too ... 1st usage of gentoo (2006 release), and it totally destroyed my setup [ grub install C-R-A-S-H-E-D ] ... :???:

happily using sabayon 3.2 now w/ NO issues [ beryl is fun ] :p

---

### Post by thePuck on 2006-12-17
Sabayon does some weird stuff to my box...something related to video. Sometimes it'll happen at boot and sometimes when I change a theme or something video related. It gives me a hard boot and the motherboard siren goes off. So even though it looked like a nice distro, after several attempts I gave up.

---

### Post by RAV TUX on 2006-12-17
All I have to say is you won't be at all impressed by the E16 screenshot.....this desktop is 1000% customizable the Sabayon devs have left it to the user to customize....first time that I can remember booting into E16....

diffinately a learning curve for me....but this desktop is lightening fast!

faster the Fluxbox!

wow!

---

### Post by RAV TUX on 2006-12-17
> **thePuck said:**
> Sabayon does some weird stuff to my box...something related to video. Sometimes it'll happen at boot and sometimes when I change a theme or something video related. It gives me a hard boot and the motherboard siren goes off. So even though it looked like a nice distro, after several attempts I gave up.
  you have to>  emerge --sync after install...

and run layman

it's all in the Sabayon Wiki and forum....and Google works wonders....remember everything that works for Gentoo is true for Sabayon...so search and you will find...if not by default Sabayon includes a "get live help" icon on the desktop that takes you to #sabayon IRC channel...it couldn't get much easier

---

### Post by RAV TUX on 2006-12-17
Default is KDE....

[[IMG]http://img344.imageshack.us/img344/654/snapshot7cn8.th.png[/IMG]](http://img344.imageshack.us/my.php?image=snapshot7cn8.png)

---

### Post by yabbadabbadont on 2006-12-17
> **RAV TUX said:**
> All I have to say is you won't be at all impressed by the E16 screenshot.....this desktop is 1000% customizable the Sabayon devs have left it to the user to customize....first time that I can remember booting into E16....

diffinately a learning curve for me....but this desktop is lightening fast!

faster the Fluxbox!

wow!
E16 and E17 are insane when it comes to the "snappiness factor".  It's just that E16 is a bit outdated and they can't stop changing fundamental things inside of E17.  I've run E17 from cvs a few times but you never know if it is going to work the next time you pull the source down.  I've been running Fluxbox from svn for quite a while now and it has never failed to build and run.  (and I update it from svn once a week)  OK, end of rant.  :lol:

---

### Post by RAV TUX on 2006-12-17
> **yabbadabbadont said:**
> E16 and E17 are insane when it comes to the "snappiness factor".  It's just that E16 is a bit outdated and they can't stop changing fundamental things inside of E17.  I've run E17 from cvs a few times but you never know if it is going to work the next time you pull the source down.  I've been running Fluxbox from svn for quite a while now and it has never failed to build and run.  (and I update it from svn once a week)  OK, end of rant.  :lol:
  I am delayed in my screenshot tour...I was showing my wife the different desktops and she fell in love with Fluxbox....she said it is a dream come true...

she hates icons and list of programs...

she is playing a game on E16...Gnometris....right now on Sabayon....so I am writing from her Fujitsu convertible....which she wants me to load Sabayon so she can use Fluxbox.....

I will do it one day but as a dual boot...

I have spoken to the Sabayon Devs and they tell me that Sabayon is built by default to work on the Wacom tablets....these guys are pure genius.

---

### Post by RAV TUX on 2006-12-17
Ok custom...I have not set up yet....and I have included screenshots in other threads of Beryl on KDE..

Failsafe just takes you to a terminal...

*moving this thread to Gentoo(and derivatives) forum.*

---

### Post by slimdog360 on 2006-12-17
I tried the enlightenment (E16) desktop a few months ago. I really did like it but found that it lacked many a feature which I need in a desktop environment. But it certainly looked promising (and pretty).

---

### Post by mips on 2006-12-17
> **yabbadabbadont said:**
> E16 and E17 are insane when it comes to the "snappiness factor".  It's just that E16 is a bit outdated and they can't stop changing fundamental things inside of E17.  I've run E17 from cvs a few times but you never know if it is going to work the next time you pull the source down.  I've been running Fluxbox from svn for quite a while now and it has never failed to build and run.  (and I update it from svn once a week)  OK, end of rant.  :lol:

Here is the e17 howto for sabayon:
[http://www.sabayonlinux.org/forum/viewtopic.php?t=826](http://www.sabayonlinux.org/forum/viewtopic.php?t=826)

---

### Post by RAV TUX on 2006-12-17
> **mips said:**
> Here is the e17 howto for sabayon:
[http://www.sabayonlinux.org/forum/viewtopic.php?t=826](http://www.sabayonlinux.org/forum/viewtopic.php?t=826)

Thanks mips8)

---

### Post by RAV TUX on 2006-12-17
also well documented here:

[http://gentoo-wiki.com/HOWTO_emerge_e17](http://gentoo-wiki.com/HOWTO_emerge_e17)

---

### Post by hikaricore on 2006-12-18
I recently refered a friend to sabayon linux, after attempting to get him to use ubuntu, I realize he doesn't have the time or effort into installing all the chite ubuntu requires just to make everything "non-free" work.  And from what I've seen in sabayon this is all done by default.  Noticing this post about being able to choose desktop environments so easily as they're all availible by default should make it an even easier switch for him from windows.  :)

---

### Post by RAV TUX on 2006-12-30
> **hikaricore said:**
> I recently refered a friend to sabayon linux, after attempting to get him to use ubuntu, I realize he doesn't have the time or effort into installing all the chite ubuntu requires just to make everything "non-free" work.  And from what I've seen in sabayon this is all done by default.  Noticing this post about being able to choose desktop environments so easily as they're all availible by default should make it an even easier switch for him from windows.  :)

Simply Awesome!...

---

### Post by d3v1ant_0n3 on 2006-12-30
The Sabayon Mini edition (the 3.1 that I have at least) installs KDE and Fluxbox by default. I couldn't even get the DVD edition to start installing for me. The cd version installed very well as a single boot, and it all worked stunningly well, but I couldn't get my head around emerge. Might give it a try as a dual boot sometime soon tho.

---

### Post by RAV TUX on 2006-12-30
> **d3v1ant_0n3 said:**
> The Sabayon Mini edition (the 3.1 that I have at least) installs KDE and Fluxbox by default. I couldn't even get the DVD edition to start installing for me. The cd version installed very well as a single boot, and it all worked stunningly well, but I couldn't get my head around emerge. Might give it a try as a dual boot sometime soon tho.

emerge is simply the easiest...

If you need emerge help let me know....here is some emerge help:

>  emerge -help


Usage:
   emerge [ options ] [ action ] [ ebuildfile | tbz2file | dependency ] [ ... ]
   emerge [ options ] [ action ] < system | world >
   emerge < --sync | --metadata | --info >
   emerge --resume [ --pretend | --ask | --skipfirst ]
   emerge --help [ system | world | config | --sync ]
Options: -[abBcCdDefgGhikKlnNoOpqPsStuvV] [--oneshot] [--newuse] [--noconfmem]
                                          [ --color < y | n >  ] [ --columns ]
                                                                 [--nospinner]
                                          [ --deep  ] [--with-bdeps < y | n > ]
Actions: [ --clean | --depclean | --prune | --regen | --search | --unmerge ]


Help (this screen):
       --help (-h short option)
              Displays this help; an additional argument (see above) will tell
              emerge to display detailed help.

Actions:
       --clean (-c short option)
              Cleans the system by removing outdated packages which will not
              remove functionalities or prevent your system from working.
              The arguments can be in several different formats :
              * world
              * system or
              * 'dependency specification' (in single quotes is best.)
              Here are a few examples of the dependency specification format:
              binutils matches
                  binutils-2.11.90.0.7 and binutils-2.11.92.0.12.3-r1
              sys-devel/binutils matches
                  binutils-2.11.90.0.7 and binutils-2.11.92.0.12.3-r1
              >sys-devel/binutils-2.11.90.0.7 matches
                  binutils-2.11.92.0.12.3-r1
              >=sys-devel/binutils-2.11.90.0.7 matches
                  binutils-2.11.90.0.7 and binutils-2.11.92.0.12.3-r1
              <=sys-devel/binutils-2.11.92.0.12.3-r1 matches
                  binutils-2.11.90.0.7 and binutils-2.11.92.0.12.3-r1

       --config
              Runs package-specific operations that must be executed after an
              emerge process has completed.  This usually entails configuration
              file setup or other similar setups that the user may wish to run.

       --depclean
              Cleans the system by removing packages that are not associated
              with explicitly merged packages. Depclean works by creating the
              full dependency tree from the system list and the world file,
              then comparing it to installed packages. Packages installed, but
              not associated with an explicit merge are listed as candidates
              for unmerging. WARNING: This can seriously affect your system by
              removing packages that may have been linked against, but due to
              changes in USE flags may no longer be part of the dep tree. Use
              caution when employing this feature.

       --info
              Displays important portage variables that will be exported to
              ebuild.sh when performing merges. This information is useful
              for bug reports and verification of settings. All settings in
              make.{conf,globals,defaults} and the environment show up if
              run with the '--verbose' flag.

       --metadata
              Causes portage to process all the metacache files as is normally
              done on the tail end of an rsync update using emerge --sync.
              This processing creates the cache database that portage uses for
              pre-parsed lookups of package data.

       --prune (-P short option)
              WARNING: This action can remove important packages!
              Removes all but the most recently installed version of a package
              from your system. This action doesn't verify the possible binary
              compatibility between versions and can thus remove essential
              dependencies from your system.
              The argument format is the same as for the --clean action.

       --regen
              Causes portage to check and update the dependency cache of all
              ebuilds in the portage tree. This is not recommended for rsync
              users as rsync updates the cache using server-side caches.
              Rsync users should simply 'emerge --sync' to regenerate.

       --resume
              Resumes the last merge operation. It can be treated just like a
              regular emerge: --pretend and other options work alongside it.
              'emerge --resume' only returns an error on failure. When there is
              nothing to do, it exits with a message and a success condition.

       --search (-s short option)
              Searches for matches of the supplied string in the current local
              portage tree. By default emerge uses a case-insensitive simple
              search, but you can enable a regular expression search by
              prefixing the search string with %%.
              Prepending the expression with a '@' will cause the category to
              be included in the search.
              A few examples:
              emerge --search libc
                  list all packages that contain libc in their name
              emerge --search '%^kde'
                  list all packages starting with kde
              emerge --search '%gcc$'
                  list all packages ending with gcc
              emerge --search '%@^dev-java.*jdk'
                  list all available Java JDKs

       --searchdesc (-S short option)
              Matches the search string against the description field as well
              the package's name. Take caution as the descriptions are also
              matched as regular expressions.
                emerge -S html
                emerge -S applet
                emerge -S 'perl.*module'

       --unmerge (-C short option)
              WARNING: This action can remove important packages!
              Removes all matching packages completely from
              your system. Specify arguments using the dependency specification
              format described in the --clean action above.

       --update (-u short option)
              Updates packages to the best version available, which may not
              always be the highest version number due to masking for testing
              and development. This will also update direct dependencies which
              may not what you want. Package atoms specified on the command line
              are greedy, meaning that unspecific atoms may match multiple
              installed versions of slotted packages.

       --version (-V short option)
              Displays the currently installed version of portage along with
              other information useful for quick reference on a system. See
              emerge info for more advanced information.

Options:
       --alphabetical
              When displaying USE and other flag output, combines the enabled
              and disabled flags into a single list and sorts it alphabetically.
              With this option, output such as USE="dar -bar -foo" will instead
              be displayed as USE="-bar dar -foo"

       --ask (-a short option)
              before performing the merge, display what ebuilds and tbz2s will
              be installed, in the same format as when using --pretend; then
              ask whether to continue with the merge or abort. Using --ask is
              more efficient than using --pretend and then executing the same
              command without --pretend, as dependencies will only need to be
              calculated once. WARNING: If the "Enter" key is pressed at the
              prompt (with no other input), it is interpreted as acceptance of
              the first choice.  Note that the input buffer is not cleared prior
              to the prompt, so an accidental press of the "Enter" key at any
              time prior to the prompt will be interpreted as a choice!

       --buildpkg (-b short option)
              Tell emerge to build binary packages for all ebuilds processed
              (in addition to actually merging the packages.  Useful for
              maintainers or if you administrate multiple Gentoo Linux
              systems (build once, emerge tbz2s everywhere) as well as disaster
              recovery.

       --buildpkgonly (-B short option)
              Creates a binary package, but does not merge it to the
              system. This has the restriction that unsatisfied dependencies
              must not exist for the desired package as they cannot be used if
              they do not exist on the system.

       --changelog (-l short option)
              When pretending, also display the ChangeLog entries for packages
              that will be upgraded.

       --color < y | n >
              Enable or disable color output. This option will override NOCOLOR
              (see make.conf(5)) and may also be used to force color output when
              stdout is not a tty (by default, color is disabled unless stdout
              is a tty).

       --columns
              Display the pretend output in a tabular form. Versions are
              aligned vertically.

       --debug (-d short option)
              Tell emerge to run the ebuild command in --debug mode. In this
              mode, the bash build environment will run with the -x option,
              causing it to output verbose debug information print to stdout.
              --debug is great for finding bash syntax errors as providing
              very verbose information about the dependency and build process.

       --deep (-D short option)
              This flag forces emerge to consider the entire dependency tree of
              packages, instead of checking only the immediate dependencies of
              the packages. As an example, this catches updates in libraries
              that are not directly listed in the dependencies of a package.
              Also see --with-bdeps for behavior with respect to build time
              dependencies that are not strictly required.

       --emptytree (-e short option)
              Virtually tweaks the tree of installed packages to contain
              nothing. This is great to use together with --pretend. This makes
              it possible for developers to get a complete overview of the
              complete dependency tree of a certain package.

       --fetchonly (-f short option)
              Instead of doing any package building, just perform fetches for
              all packages (main package as well as all dependencies.) When
              used in combination with --pretend all the SRC_URIs will be
              displayed multiple mirrors per line, one line per file.

       --fetch-all-uri (-F short option)
              Same as --fetchonly except that all package files, including those
              not required to build the package, will be processed.

       --getbinpkg (-g short option)
              Using the server and location defined in PORTAGE_BINHOST, portage
              will download the information from each binary file there and it
              will use that information to help build the dependency list. This
              option implies '-k'. (Use -gK for binary-only merging.)

       --getbinpkgonly (-G short option)
              This option is identical to -g, as above, except it will not use
              ANY information from the local machine. All binaries will be
              downloaded from the remote server without consulting packages
              existing in the packages directory.

       --newuse (-N short option)
              Tells emerge to include installed packages where USE flags have
              changed since installation.

       --noconfmem
              Portage keeps track of files that have been placed into
              CONFIG_PROTECT directories, and normally it will not merge the
              same file more than once, as that would become annoying. This
              can lead to problems when the user wants the file in the case
              of accidental deletion. With this option, files will always be
              merged to the live fs instead of silently dropped.

       --nodeps (-O short option)
              Merge specified packages, but don't merge any dependencies.
              Note that the build may fail if deps aren't satisfied.

       --noreplace (-n short option)
              Skip the packages specified on the command-line that have
              already been installed.  Without this option, any packages,
              ebuilds, or deps you specify on the command-line *will* cause
              Portage to remerge the package, even if it is already installed.
              Note that Portage won't remerge dependencies by default.

       --nospinner
              Disables the spinner regardless of terminal type.

       --oneshot (-1 short option)
              Emerge as normal, but don't add packages to the world profile.
              This package will only be updated if it is depended upon by
              another package.

       --onlydeps (-o short option)
              Only merge (or pretend to merge) the dependencies of the
              specified packages, not the packages themselves.

       --pretend (-p short option)
              Instead of actually performing the merge, simply display what
              ebuilds and tbz2s *would* have been installed if --pretend
              weren't used.  Using --pretend is strongly recommended before
              installing an unfamiliar package.  In the printout, N = new,
              U = updating, R = replacing, F = fetch  restricted, B = blocked
              by an already installed package, D = possible downgrading,
              S = slotted install. --verbose causes affecting use flags to be
              printed out accompanied by a '+' for enabled and a '-' for
              disabled USE flags.

       --quiet (-q short option)
              Effects vary, but the general outcome is a reduced or condensed
              output from portage's displays.

       --skipfirst
              This option is only valid in a resume situation. It removes the
              first package in the resume list so that a merge may continue in
              the presence of an uncorrectable or inconsequential error. This
              should only be used in cases where skipping the package will not
              result in failed dependencies.

       --tree (-t short option)
              Shows the dependency tree using indentation for dependencies.
              The packages are also listed in reverse merge order so that
              a package's dependencies follow the package. Only really useful
              in combination with --emptytree, --update or --deep.

       --usepkg (-k short option)
              Tell emerge to use binary packages (from $PKGDIR) if they are
              available, thus possibly avoiding some time-consuming compiles.
              This option is useful for CD installs; you can export
              PKGDIR=/mnt/cdrom/packages and then use this option to have
              emerge "pull" binary packages from the CD in order to satisfy
              dependencies.

       --usepkgonly (-K short option)
              Like --usepkg above, except this only allows the use of binary
              packages, and it will abort the emerge if the package is not
              available at the time of dependency calculation.

       --verbose (-v short option)
              Effects vary, but the general outcome is an increased or expanded
              display of content in portage's displays.

       --with-bdeps < y | n >
              In dependency calculations, pull in build time dependencies that
              are not strictly required. This defaults to 'n' for installation
              actions and 'y' for the --depclean action. This setting can be
              added to EMERGE_DEFAULT_OPTS (see make.conf(5)) and later
              overridden via the command line.

---

### Post by d3v1ant_0n3 on 2006-12-30
So to do the equivalent of ```
sudo aptitude upgrade
``` I would do```
 su
emerge --update
```
?

The only distros I've used for any length of time (i.e. more than a day) have been K/X/Ubuntu and Mepis, so I'm kinda used to the aptitude way of doing things.

---

### Post by RAV TUX on 2006-12-31
> **d3v1ant_0n3 said:**
> So to do the equivalent of ```
sudo aptitude upgrade
``` I would do```
 su
emerge --update
```?

The only distros I've used for any length of time (i.e. more than a day) have been K/X/Ubuntu and Mepis, so I'm kinda used to the aptitude way of doing things.

actually I would suggest an option for which Debian systems do NOT have an equivalent for...but proper etiquette dictates you only do it once a day:
> 
emerge --syncremember:


>         --update (-u short option)
              Updates packages to the best version available, [COLOR=Red]which may not
              always be the highest version number due to masking for testing
              and development. This will also update direct dependencies which
              may not be what you want.[/COLOR] Package atoms specified on the command line
              are greedy, meaning that unspecific atoms may match multiple
              installed versions of slotted packages.

---

### Post by RAV TUX on 2006-12-31
> **RAV TUX said:**
> actually I would suggest an option for which Debian systems do NOT have an equivalent for...but proper etiquette dictates you only do it once a day:
remember:

after

>  emerge --sync

remember to:

 > emerge portage

---

### Post by d3v1ant_0n3 on 2006-12-31
> **RAV TUX said:**
> after



remember to:


I managed to do the emerge --sync (and even got the etiquette warning:P ), but I genuinely wasn't sure about what to do next (i worked --sync out to be the equivalent of aptitude update). I ran Portage, but there was no blindingly obvious 'Update system' type button.

One more (somewhat off topic but not) question (for now). Partitioning. Am I right in thinking I can just resize my existing partition, make a new / partition for sabayon and it will automatically add itsef to GRUB?

---

### Post by RAV TUX on 2006-12-31
> **d3v1ant_0n3 said:**
> I managed to do the emerge --sync (and even got the etiquette warning:P ), but I genuinely wasn't sure about what to do next (i worked --sync out to be the equivalent of aptitude update). I ran Portage, but there was no blindingly obvious 'Update system' type button.

One more (somewhat off topic but not) question (for now). Partitioning. Am I right in thinking I can just resize my existing partition, make a new / partition for sabayon and it will automatically add itsef to GRUB?

I would stop trying to find equivalants to and simply learn how Gentoo works and roll with it...

here is the Gentoo=netiquette warning:


> Please note: common gentoo-netiquette says you should not sync more
than once a day.  Users who abuse the rsync.gentoo.org rotation
may be added to a temporary ban list.

to you other question, I would believe so, but it depends on how you set it up.

---

### Post by RAV TUX on 2006-12-31
I just ran 

> emerge --sync

here is the outcome:


> 
sent 14845 bytes  received 4982947 bytes  38297.26 bytes/sec
total size is 158990521  speedup is 31.81

>>> Updating Portage cache:  100%
 * IMPORTANT: 1 config files in '/etc' need updating.
 * Type emerge --help config to learn how to update config files.

q: Updating ebuild cache ...
q: Finished 23713 entries in 0.614863 seconds

 * An update to portage is available. It is _highly_ recommended
 * that you update portage now, before any other packages are updated.
 * Please run 'emerge portage' and then update ALL of your
 * configuration files.
 * To update portage, run 'emerge portage'.

it is important to follow the instructions given.

---

### Post by RAV TUX on 2006-12-31
here is the out put of:

> emerge --help config

> 
 emerge --help config
*** Deprecated use of action 'config', use '--config' instead
*** Deprecated use of action 'config', use '--config' instead
Config file management support (preliminary)

Portage has a special feature called "config file protection".  The purpose of
this feature is to prevent new package installs from clobbering existing
configuration files.  By default, config file protection is turned on for /etc
and the KDE configuration dirs; more may be added in the future.

When Portage installs a file into a protected directory tree like /etc, any
existing files will not be overwritten.  If a file of the same name already
exists, Portage will change the name of the to-be-installed file from 'foo' to
'._cfg0000_foo'.  If '._cfg0000_foo' already exists, this name becomes
'._cfg0001_foo', etc.  In this way, existing files are not overwritten,
allowing the administrator to manually merge the new config files and avoid any
unexpected changes.

In addition to protecting overwritten files, Portage will not delete any files
from a protected directory when a package is unmerged.  While this may be a
little bit untidy, it does prevent potentially valuable config files from being
deleted, which is of paramount importance.

Protected directories are set using the CONFIG_PROTECT variable, normally
defined in /etc/make.globals.  Directory exceptions to the CONFIG_PROTECTed
directories can be specified using the CONFIG_PROTECT_MASK variable.  To find
files that need to be updated in /etc, type:

# find /etc -iname '._cfg????_*'

You can disable this feature by setting CONFIG_PROTECT="-*" in /etc/make.conf.
Then, Portage will mercilessly auto-update your config files.  Alternatively,
you can leave Config File Protection on but tell Portage that it can overwrite
files in certain specific /etc subdirectories.  For example, if you wanted
Portage to automatically update your rc scripts and your wget configuration,
but didn't want any other changes made without your explicit approval, you'd
add this to /etc/make.conf:

CONFIG_PROTECT_MASK="/etc/wget /etc/rc.d"

Tools such as dispatch-conf, cfg-update, and etc-update are also available to
aid in the merging of these files. They provide interactive merging and can
auto-merge trivial changes.

---

### Post by SOS986 on 2007-01-12
the grub,partitioner, nearly everything about sabayon was much simpler for me to use, i believe if you make a dual booting machine you'll have your hand held through the grub configuration process, after being asked if you want to keep your old one, or get the one that comes with sabayon. i was VERY impressed with sabayon i can't stress that enough, imo everyone that has ubuntu installed on the pc, should install this as well theres no better way to build experience using gentoo, portage, and emerge and better yet this is something that needs to be in your bag of tricks you can simply put this CD in a your buddys tray show them beryl and take it off without so much as a scratch on there hd. linux has come such a long way its really quite impressive.

---

### Post by pichalsi on 2007-01-12
I installed the Sabayon on HDD but I still use Kubuntu more for a few reasons: 
1. Beryl is very jerky in Sabayon on my system for some stupid reason i dont understand. The original beryl was, svn beryl is too, maybe i should update drivers, i dont know
2. my kubuntu is tweaked great for my needs cause i use it for a long time, and for now i dont have enough time to tweak again... But i think i will try Gentoo after exams :) It just looks challenging for me ;)

---

### Post by RAV TUX on 2007-01-12
> **pichalsi said:**
> I installed the Sabayon on HDD but I still use Kubuntu more for a few reasons: 
1. Beryl is very jerky in Sabayon on my system for some stupid reason i dont understand. The original beryl was, svn beryl is too, maybe i should update drivers, i dont know
2. my kubuntu is tweaked great for my needs cause i use it for a long time, and for now i dont have enough time to tweak again... But i think i will try Gentoo after exams :) It just looks challenging for me ;)

what version Sabayon?....I found the new 3.26 to be the most reliable, with no bugs....at least none to report yet.

---

