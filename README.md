# Engineering Notebook

This script creates a topic within the enginneering notebook that I use on a day-to-day basis. Topics are laid out in the following structure:

```
topic_name/
	-> data/
	-> code/
	-> notes/
	-> README.md
```

## I did not originally come up with this idea!

I was originally inspired by the work that **[@dankleiman](https://github.com/dankleiman)** did on his [Engineering Notebook](https://github.com/dankleiman/notebook). While it worked, there were a few things that I wanted that his work didn't cover:

* When I create a new topic, I want that topic opened in my editor of choice without having to change to the directory manually.
* For editors like Sublime Text and others that support directories, I wanted the ability to recall multiple topics in a single editor instance.
* I use [tmux](https://github.com/tmux/tmux), almost religiously. If I need to open a topic, I want my editor to open in a new tmux window automatically. This allows me to create workspaces that can be dedicated solely to a given topic.
* I didn't want to construct an alias or function for the editor-opening behavior. I'd rather alias flags instead, and have the ability to re-declare a flag if I never need to override a behavior.

## Usage

```
Engineering Notebook
Scaffolds the necessary structure for taking notes related to one or more specified topic.

The Directory structure for topics is created in NOTE_PATH.
If NOTE_PATH is not set, defaults to the current working directory.

Once scaffolded, the topic will be opened in NOTE_EDITOR.
If NOTE_EDITOR is not set, defaults to VISUAL, then EDITOR, then vi.

notebook <flags> <topic>
  One or more topics can be specified.
  If no flags are specified, opens the last <topic> declared.

Flags:
  -e|--editor <exec>
    Uses <exec> instead of NOTE_EDITOR.
  -m|--multi-open
    If more than one <topic> is declared, attempt to open them all in the same editor instance.
    Useful for editors like Sublime Text, which can accept multiple folders when coupled with -p.
  -n|--note-path <path>
    Creates each <topic> in <path> instead of the current NOTE_PATH.
  -p|--open-path
    Opens the folder for each <topic>, instead of the README.md.
    Useful for editors like Sublime Text, which can accept multiple folders when coupled with -m.
  -t|--tmux
    If currently in a tmux session, opens a new tmux window for each topic.
```

**@dankleiman** described the way to use this notebook best in his version:

>The simple folder structure helps you organize ongoing work on an engineering problem.
>
> As you collect supporting data, put the files in the `data` folder. As you build small pieces of code, collect them in the `code` folder. Likewise, any note taking along the way can live in the `notes` folder.
> 
> Keep re-writing the top-level `README.md` file as you refine your understanding of the problem. Ultimately, the README evolves into the document you present to your co-workers or other stakeholders that includes a high-level overview of the problem, the steps you took in your investigation, and solution you are proposing.

## Setup

Make sure that either `NOTE_EDITOR`, `VISUAL`, or `EDITOR` is set to your preferred editor. The script will default to this editor unless you override it with `-e` or `--editor`.

Locate a place where you would like to keep your notebook on your machine, and set `NOTE_PATH` to be that location. The script will create new topics in this location unless you override it with `-n` or `--note-path`.

If you use an editor that supports opening multiple files, you may want to consider using `-m` or `--multi-open`, which will open one or more declared topics in the same instance of the editor.

Additionally, if your editor can accept a directory, you may want to consider using `-p` or `--open-path`, which will open your topics by their folder. Combining `-m` and `p` is very useful with editors like Sublime Text, giving a tree view of each topic.

If you use tmux, you may want to consider using `-t` or `--tmux`. This will open a new tmux window for each topic, launching your editor within that topic. This is useful if you would like to set aside a working space dedicated to each topic. Note that use of this flag overrides `-m`/`--multi-open`.
