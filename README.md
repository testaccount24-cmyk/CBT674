# CBT674
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 674 is from Robin Murray and contains a nice collection   *   FILE 674
//*           of REXX-based utilities to help enhance your TSO      *   FILE 674
//*           session toolbox.  Below is a description of the       *   FILE 674
//*           tools in detail.                                      *   FILE 674
//*                                                                 *   FILE 674
//*           email   :  mvs@robinandmariette.com                   *   FILE 674
//*           web site:  http://www.robinandmariette.com            *   FILE 674
//*                                                                 *   FILE 674
//*     These utilities have been tested using OS/390 2.10 as       *   FILE 674
//*     of March 2004.  They will be tested on z/OS 1.4 as soon     *   FILE 674
//*     as possible.                                                *   FILE 674
//*                                                                 *   FILE 674
//*     These utilities are provided as is with no warranties       *   FILE 674
//*     or guarantees of any kind whatsoever.  Use at your own      *   FILE 674
//*     risk!                                                       *   FILE 674
//*                                                                 *   FILE 674
//*     ---------------------------------------------------------   *   FILE 674
//*                                                                 *   FILE 674
//*     Copied from                                                 *   FILE 674
//*     www.robinandmariette.com/Mvs/Rexx/RexxUtils.asp             *   FILE 674
//*                                                                 *   FILE 674
//*     Robin Murray's Rexx Tools/Utilities                         *   FILE 674
//*                                                                 *   FILE 674
//*     The libraries are in xmit format.  To install:              *   FILE 674
//*                                                                 *   FILE 674
//*         * Follow the instructions in the $RUNME member to       *   FILE 674
//*           recieve the rest of the libs.                         *   FILE 674
//*         * In the SAMPLIB dataset, follow the directions in      *   FILE 674
//*           members $INSTALL, $IVP, and $INSTAL2, in that         *   FILE 674
//*           order.                                                *   FILE 674
//*         * If installing SVCDUMPS, follow the directions in      *   FILE 674
//*           members $INSTALL, and $IVP of                         *   FILE 674
//*           MA133.TSO.SVCDUMPS.SYSEXEC.                           *   FILE 674
//*                                                                 *   FILE 674
//*     Last updated:  8-May-2004                                   *   FILE 674
//*                                                                 *   FILE 674
//*     Utility  Description                                        *   FILE 674
//*                                                                 *   FILE 674
//*     $START   A model for starting most reasonably complex       *   FILE 674
//*              programs.  Just copy this into your new member     *   FILE 674
//*              and begin customizing it.  For details on why      *   FILE 674
//*              I start rexx programs this way, see my hints       *   FILE 674
//*              and tips section.                                  *   FILE 674
//*                                                                 *   FILE 674
//*     $TBDISPL A model to display an ISPF table.  Copy this       *   FILE 674
//*              code into your program and make a few              *   FILE 674
//*              adjustments to display your table.  Contains       *   FILE 674
//*              boiler plate code for handling both primary        *   FILE 674
//*              and line commands.                                 *   FILE 674
//*                                                                 *   FILE 674
//*     APARSTRP A program to strip off the comments from CA        *   FILE 674
//*              supplied PTFs.  Used in conjunction with           *   FILE 674
//*              EACHMEM and possibly FTPPDS.                       *   FILE 674
//*                                                                 *   FILE 674
//*     COMPRESS A program to compress a PDS.  Can be run either    *   FILE 674
//*              as an edit macro or as a TSO exec.  Useful when    *   FILE 674
//*              you get out of space errors while in edit:         *   FILE 674
//*              simply enter COMPRESS on the command line and      *   FILE 674
//*              save again.                                        *   FILE 674
//*                                                                 *   FILE 674
//*     DELALL   Deletes all datasets beginning with the passed     *   FILE 674
//*              high level qualifier(s).  Uses ISPF 3.4            *   FILE 674
//*              masking if ISPF is active for greater              *   FILE 674
//*              flexibility.                                       *   FILE 674
//*                                                                 *   FILE 674
//*     DUPMEM   Checks for duplicate members of a concatenation.   *   FILE 674
//*              Pass the DDName of the concatanation and a card    *   FILE 674
//*              deck will be generated that can be fed to the      *   FILE 674
//*              PDS program to delete them.  LINKLIST and          *   FILE 674
//*              LPALIST can also be passed as the DDName, and      *   FILE 674
//*              the current, in-storage concatenation will be      *   FILE 674
//*              checked.                                           *   FILE 674
//*                                                                 *   FILE 674
//*     EACHMEM  To process a PDS by calling the passed rexx        *   FILE 674
//*              program for each member.  It's meant as a          *   FILE 674
//*              generalized service to process all members of      *   FILE 674
//*              a PDS.                                             *   FILE 674
//*                                                                 *   FILE 674
//*     FTPPDS   A utility to ftp a remote directory to a PDS       *   FILE 674
//*              or a PDS to a remote directory.  Uses a            *   FILE 674
//*              profile dataset to store the commands to be        *   FILE 674
//*              executed.  Can be run in batch or online.          *   FILE 674
//*                                                                 *   FILE 674
//*     GO       A simple edit macro to execute the member you      *   FILE 674
//*              are editing.  Simply enter GO on the command       *   FILE 674
//*              line along with any parms to execute your          *   FILE 674
//*              program.  Pending changes are automatically        *   FILE 674
//*              saved before the exec is run.  If the save         *   FILE 674
//*              fails, a compress is run and the save is           *   FILE 674
//*              attempted again.                                   *   FILE 674
//*                                                                 *   FILE 674
//*     NJ       To navigate through lengthy and complex JCL.       *   FILE 674
//*              Front-ends CA's JCLCHECK product with several      *   FILE 674
//*              ISPF tables.  Presents several different views     *   FILE 674
//*              of the JCL including datasets, programs,           *   FILE 674
//*              procedures, reports, and JCL errors.  Allows you   *   FILE 674
//*              to select any line to take you to the exact JCL    *   FILE 674
//*              source line to which it corresponds, no matter     *   FILE 674
//*              if it's in stream or in a procedure.  Allows you   *   FILE 674
//*              to zoom in to datasets on the dataset view.  See   *   FILE 674
//*              the job navigator section for more details on      *   FILE 674
//*              this powerful utility.                             *   FILE 674
//*                                                                 *   FILE 674
//*     QUOTES   A simple edit macro to flag lines that have        *   FILE 674
//*              uneven or missing quotes.                          *   FILE 674
//*                                                                 *   FILE 674
//*     RESTART  An IOF rexx to process the joblog and create a     *   FILE 674
//*              series of IDCAMS delete statements so that you     *   FILE 674
//*              can restart the job.                               *   FILE 674
//*                                                                 *   FILE 674
//*     SAVELIB  A quick way to make a backup copy of a PDS.        *   FILE 674
//*                                                                 *   FILE 674
//*     SORTTB   To sort any ISPF table passed to it.  Pops up      *   FILE 674
//*              a small panel where you can select Ascending       *   FILE 674
//*              or Decsending sort sequences on any field in       *   FILE 674
//*              the table.  A good utility to call from            *   FILE 674
//*              another program to allow complex sorting on a      *   FILE 674
//*              table.                                             *   FILE 674
//*                                                                 *   FILE 674
//*     SRCHGO   Used in the Search-For IBM utility to allow        *   FILE 674
//*              you to zoom in from the lines in the search        *   FILE 674
//*              results list to edit the target dataset where      *   FILE 674
//*              the line was found.                                *   FILE 674
//*                                                                 *   FILE 674
//*     STARTUP  An ISPF session manager to allow you to create     *   FILE 674
//*              and easily navigate thru many concurrent ISPF      *   FILE 674
//*              sessions.  Combines the functionality of the       *   FILE 674
//*              ISPF START, SCRNAME, SWAP LIST, and SWAP XXX       *   FILE 674
//*              command into one easy to remember command.         *   FILE 674
//*              Allows dynamic command tables to be built for      *   FILE 674
//*              each individual user.  See the startup command     *   FILE 674
//*              section for more details.                          *   FILE 674
//*                                                                 *   FILE 674
//*     SWIMACRO A sample site-wide initial edit macro showing      *   FILE 674
//*              how to create special protection for certain       *   FILE 674
//*              key system datasets like SYS1.PARMLIB and          *   FILE 674
//*              others.  Ensures that AUTOSAVE is OFF for          *   FILE 674
//*              these particular datasets so that any changes      *   FILE 674
//*              will require a manual SAVE command before          *   FILE 674
//*              leaving your edit session.                         *   FILE 674
//*                                                                 *   FILE 674
//*     CATLIBS  A new and unique way to concatenate the required   *   FILE 674
//*              TSO and ISPF libraries at logon time.  Separates   *   FILE 674
//*              products into convenient parmlib members that      *   FILE 674
//*              are assigned as needed to each user group.  It's   *   FILE 674
//*              so flexible it can hardly stand up.                *   FILE 674
//*              Automatically recovers from missing / enqueued /   *   FILE 674
//*              misspelled datasets.  See the CatLibs section      *   FILE 674
//*              for more details.                                  *   FILE 674
//*                                                                 *   FILE 674
//*     Finders  A group of find commands to quickly and easily     *   FILE 674
//*              find source library members of various sorts       *   FILE 674
//*              and by various methods.  See the find utilities    *   FILE 674
//*              section for more details on this group of very     *   FILE 674
//*              useful programs.  They are indispensible in our    *   FILE 674
//*              shop.                                              *   FILE 674
//*                                                                 *   FILE 674
//*     SVCDUMPS A modern SVC dump manager. Creates a log of        *   FILE 674
//*              your SVC dumps.  Allows ISPF table interaction     *   FILE 674
//*              with the log of dumps. Allows interactive          *   FILE 674
//*              archiving, recalling, tersing, ftping, deletion    *   FILE 674
//*              etc.  All dump management can be automated         *   FILE 674
//*              using one multi-purpose started task.              *   FILE 674
//*                                                                 *   FILE 674
```
