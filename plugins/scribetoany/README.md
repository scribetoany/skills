# scribetoany

A transcription skill for AI agents. It lets a coding agent (Claude Code,
Codex, Gemini CLI, Cursor, OpenClaw…) transcribe
audio and video files on your computer with
[ScribeToAny](https://scribetoany.com/?utm_source=github&utm_medium=readme&utm_campaign=scribetoany-cli):
text with timestamps, SRT or VTT subtitles, speaker labels, in about 98
languages. It also transcribes public X, Twitch, Loom, Google Drive and
Dropbox links.

It drives the `scribetoany` command-line tool:

```bash
npm i -g scribetoany
scribetoany auth login            # opens the browser once
scribetoany transcribe meeting.m4a --format srt
```

Add the skill in Claude Code:

```
/plugin marketplace add scribetoany/skills
/plugin install scribetoany@scribetoany-skills
```

Then ask your agent:

> Transcribe `~/Desktop/interview.m4a` with speaker labels and save it as SRT.

> 把桌面上的 lecture.mp4 转成文字稿。

## What it runs, sends and stores

- **Runs:** the `scribetoany` CLI from npm (Node.js 20 or later). The agent
  asks you before it installs it globally; otherwise it runs a pinned
  `npx -y scribetoany@0.1.6`. The plugin has no hooks and no MCP server for
  Claude Code.
- **Signs in:** `scribetoany auth login` opens scribetoany.com in your browser,
  where you sign in and approve "ScribeToAny CLI". The access token is saved
  on your computer in `~/.config/scribetoany/credentials.json`; the skill
  tells the agent never to print or copy it.
- **Sends:** the audio or video file you ask it to transcribe, or the link
  you give it, to your ScribeToAny account at scribetoany.com, where it is
  transcribed. Nothing else on your computer is read or sent.
- **Saves:** the transcript (TXT, SRT, VTT or JSON) next to where you run it.
  On ScribeToAny the uploaded recording is deleted once it is transcribed;
  the transcript stays in your dashboard until you delete it.

You need a ScribeToAny account. Transcriptions count toward your plan (the
free plan includes 100 minutes a month). We never train AI on your files.
See the [privacy policy](https://scribetoany.com/privacy) and the
[terms](https://scribetoany.com/terms); for help, use the
[contact page](https://scribetoany.com/contact).
