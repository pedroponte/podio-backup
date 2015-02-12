podio-backup
============

Creating an incremental backup for the data stored it Podio (including files).

Forked from https://github.com/daniel-sc/podio-backup

The differences are:
The backup will download always to the same folder (i.e., no timestamp) so you can push daily the changes to a git repository.
The memory size limit was increased to 500M to support larger podio repositories.

Script from daniel-sc originally based on:
-------------------------

This runs as php commandline script (cli) and is based on: http://www.podiomail.com/blog/easy-podio-full-backup.php (thanks!)

A superior (hosted) backup solution is found at https://www.cloud-backup-for-podio.com (check it out!).

Features include:
-------------------------
- _Incremental backup_ (files are downloaded only once and are linked on subsequent runs).
- Stores item human readable _including comments_ - additionally items are bulk downloaded as excel file.
- All files hosted at Podio are downloaded, files hosted externally are linked and easily accessible in an html app overview.
- Smart handling of rate limits (sleeps before hitting the podio rate limit).

Usage:
----------
    php podio_backup_full_cli.php [-f] [-v] [-s PARAMETER_FILE] --backupTo BACKUP_FOLDER --podioClientId PODIO_CLIENT_ID --podioClientSecret PODIO_CLIENT_SECRET --podioUser PODIO_USERNAME --podioPassword PODIO_PASSWORD
    
    php podio_backup_full_cli.php [-f] [-v] -l PARAMETER_FILE [--backupTo BACKUP_FOLDER] [--podioClientId PODIO_CLIENT_ID] [--podioClientSecret PODIO_CLIENT_SECRET] [--podioUser PODIO_USERNAME] [--podioPassword PODIO_PASSWORD]

    php podio_backup_full_cli.php --help

    Arguments:
       -f	download files from podio (rate limit of 250/h applies!)
       -v	verbose
       -s	store parameters in PARAMETER_FILE
       -l	load parameters from PARAMETER_FILE (parameters can be overwritten by command line parameters)
     
    BACKUP_FOLDER represents the incremental backup storage, i.e. consecutive backups will only download new files and update podio items info locally in a csv file.
    The backup will download always to the same folder (i.e., no timestamp) so you can push daily  changes to a git repository.

Installation:
------------------
After cloning the repository don't forget to initialize the podio-php submodule via:
`git submodule init` and subsequent `git submodule update`.
