---
name: claude-code-onboarding
description: A kind, step-by-step guide for people who have never used a terminal. It takes them from nothing to a live website. It installs Claude Code, explains how much Claude should ask before it acts (plan, accept edits, auto and the other modes), helps them design the site first on an editable design board, builds it with Astro, and puts it on the internet with Vercel. Use when someone says "help me get started with Claude Code", "I am not technical", "install Claude Code for me", "what is plan mode", "how do I build and host a website", "set me up with Astro and Vercel", or "onboard me". Works inside Claude Code and also inside a normal Claude chat, before Claude Code is installed.
---

# Start here: from zero to a live website with Claude Code

This guide is for people who are not technical. The person may have no terminal skills, no Homebrew, no Node.js and no idea where to look when something goes wrong. That is fine. Everyone starts here.

By the end, the person will have:

1. Claude Code installed on their computer.
2. A clear idea of how much Claude should ask before it acts, and how to change that.
3. A design for their website, made on an editable design board that they can click and change.
4. A simple website that they built with Astro, from that design.
5. The website live on the internet with Vercel, at a web address they can share.
6. A clear idea of where to look when something goes wrong.

## Your role: how to guide

Read this section first. It matters more than any command.

- **Be kind and calm.** The person may feel nervous. Say that errors are normal and that every expert sees them every day. Never make the person feel slow.
- **Go one step at a time.** Give one step. Wait for the person to say it is done. Then give the next step. Do not show the whole guide at once.
- **Explain why in 1 sentence.** Say what a command does before the person types it. Do not use a technical word without a short, plain explanation.
- **Show every command in a code block,** so the person can copy and paste it.
- **Say what success looks like.** After each command, tell the person what they should see. Then they know it worked.
- **Praise small wins.** "That worked. Well done." is enough.
- **A "yes" is not proof.** After a command that you need to see the result of, such as a version check, "yeah", "ok" or "done" is not enough. Ask: "Could you paste what it shows, so I can be sure?" Only move on when you have seen the output, or the person describes it clearly.
- **Always teach Plan mode and Accept edits.** Do this even if the person wants to skip ahead. Teach them in Part 4, and at the latest before the first build in Part 6. They are the most useful habits in Claude Code. Plan mode first saves time and tokens, because Claude thinks before it types and the person can fix the idea before any work is done.
- **One action at a time.** Give 1 command block and 1 check in each message. Do not bundle install, restart and check into one message for a nervous person.
- **Never ask the person to guess.** If you are not sure what their screen shows, ask them to copy the text and paste it to you.
- **Keep sentences short.** Use plain words.
- **If the person is afraid of the terminal,** be extra gentle. Say that nothing happens until they push Enter. Offer the Code tab of the Claude desktop app first (https://claude.ai/download), where you can run the commands for them.
- **Always give the link.** When a step tells the person to open a website to do something, write the full link in that step, for example https://vercel.com/signup. Never write only "go to Vercel". The link must be easy to click.
- **Use the right model for each job.** If you start a helper (subagent) during this guide, follow "Which model for which job" in Part 4. Check a helper's work before you tell the person that it is done. A helper never starts more helpers.

### Which mode are you in?

- **Claude Code mode.** You have a Bash tool. Run the checks yourself. Show the person what you ran. Ask permission in plain words before a change that is hard to undo.
- **Chat mode.** You have no tools, so you cannot see their computer. Give the command. Ask them to run it and paste back everything they see. Read what they paste before you decide the next step.

If a command needs a sign-in or a password, tell the person to type it in the prompt with a `!` at the start, for example `! npx vercel login`. The `!` runs the command inside this session. In chat mode, the person runs it in their own terminal.

### Start by asking 3 questions

1. "Which computer do you use: a Mac, a Windows PC or Linux?"
2. "What kind of website do you want? For example: a page about you, a small business page, a portfolio or a blog."
3. "Have you ever used a terminal before? It is fine if not."

Use the answer to question 2 for the design in Part 5 and the site in Part 6. Use the answer to question 1 for the right commands in every part.

## Words you will hear

Give the person this short list early. Come back to it when a word is new.

| Word | What it means |
|---|---|
| Terminal | A window where you type instructions to your computer instead of clicking. |
| Command | One instruction that you type in the terminal. You push Enter to run it. |
| Folder | The same as on your desktop. The terminal is always "inside" one folder. |
| Claude Code | Claude, working inside your terminal. It can read your files and change them. |
| Permission mode | A setting that says how much Claude can do before it asks you. |
| Node.js | A free tool that some programs need to run. Astro needs it. |
| Design board | A page where you click text, colours and fonts to try a design. No code. |
| Astro | A free tool that builds fast, simple websites. |
| Vercel | A company that puts your website on the internet. The free plan is enough to start. |
| Deploy | To put your website on the internet so other people can see it. |
| Localhost | A private copy of your site that only you can see, on your own computer. |
| Checkpoint | A saved copy of your project at one moment. You can go back to it. |

## Part 1 - Open the terminal

The terminal looks plain. It cannot hurt anything until you type a command and push Enter.

- **Mac:** Push `Cmd` and `Space` together. Type `Terminal`. Push Enter.
- **Windows:** Click the Start button. Type `PowerShell`. Click "Windows PowerShell".
- **Linux:** Open the "Terminal" app from your apps.

Tell the person:

- To **paste** into the terminal: on a Mac push `Cmd` and `V`. On Windows, right-click in the window, or push `Ctrl` and `V`.
- To **run** a command: push `Enter`.
- If the terminal looks stuck, push `Ctrl` and `C` to stop it. That is safe.
- Words like `$` or `>` at the start of a line are only the prompt. They do not type them.

Quick test. Ask them to type this and push Enter:

```bash
echo "Hello"
```

They should see `Hello`. That is the first win.

## Part 2 - Install the tools

The person needs 2 things: Claude Code and Node.js. They do not need Homebrew. Do not suggest it.

### 2a. Windows only: install Git

Skip this on a Mac or Linux.

Claude Code on Windows needs a free tool called Git for Windows.

1. Open https://git-scm.com/download/win in a browser.
2. Download the installer and open it.
3. Click "Next" on every screen. The default choices are right.
4. When it ends, close PowerShell and open it again.

### 2b. Install Claude Code

On a Mac, Linux or Windows with WSL (a Linux layer in Windows), paste this:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

On Windows in PowerShell, paste this:

```powershell
irm https://claude.ai/install.ps1 | iex
```

This downloads Claude Code and puts it on the computer. It takes about a minute.

**Close the terminal. Open a new one.** This is an important step that many people miss. Then check the install:

```bash
claude --version
```

They should see a version number, such as `2.1.318`. Any number is fine.

If the terminal says `command not found: claude`, go to "When something goes wrong".

### 2c. Install Node.js

Astro needs Node.js version 22.23.4 or newer. Use an even-numbered version. The "LTS" button on the Node.js site gives the right one.

1. Open https://nodejs.org in a browser.
2. Click the big green "LTS" download button.
3. Open the file that downloads. Click "Continue" or "Next" on every screen.
4. **Close the terminal. Open a new one.**

Check the install:

```bash
node --version
npm --version
```

They should see a number like `v24.1.0` and a second number. `npm` came with Node.js. It installs other tools.

If the Node.js number is lower than 22.23.4, ask them to download the newest LTS version again from https://nodejs.org and repeat the install.

## Part 3 - Sign in to Claude Code and say hello

### 3a. Make a folder for the work

A folder keeps the work in one place. Run these 2 commands:

```bash
mkdir -p ~/websites
cd ~/websites
```

On Windows PowerShell, run this instead:

```powershell
mkdir $HOME\websites
cd $HOME\websites
```

`mkdir` makes a folder. `cd` moves into it.

### 3b. Start Claude Code

```bash
claude
```

The first time, Claude Code opens a web page and asks the person to sign in. They sign in there and come back to the terminal.

Claude Code needs a paid Claude plan (Pro or higher), or Anthropic Console credit. The free Claude plan does not include it. If the person is not sure, send them to https://claude.com/pricing to check. To make an account, they use https://claude.ai.

If Claude asks "Do you trust the files in this folder?", say yes. It is their own new folder.

### 3c. Say hello

Ask the person to type this in Claude Code and push Enter:

```
Hello! I am new to this. Please explain in simple words what you can do for me.
```

Tell them: Claude Code will sometimes ask permission before it changes a file or runs a command. This is a safety feature. Part 4 explains how to choose how often it asks.

The 4 controls to remember:

| Key or command | What it does |
|---|---|
| `Esc` | Stops Claude while it works. Safe at any time. |
| `/help` | Shows help. |
| `/clear` | Starts a fresh chat. Use it when you start a new job. |
| `/exit` or `Ctrl` and `C` twice | Leaves Claude Code. |

## Part 4 - Choose how much Claude asks first, and which model it uses

Start with a picture. Claude Code is like a helpful new assistant in your office. A permission mode is how much you trust the assistant to act without checking with you first. You can change the mode at any time, even in the middle of a job.

### The modes

| Mode | What Claude does without asking | What Claude still asks about | Best for |
|---|---|---|---|
| **Manual** (the default, also called "default") | Reads files and looks around. | Every file change, every command and every use of the internet. | Your first day. Learning what Claude does. Work with private files. |
| **Plan mode** (`plan`) | Reads and thinks only. It cannot change files until you approve a plan. | It writes a plan, then asks you to approve it. Commands still ask. | A new or big job. When you want to check the idea before any work starts. |
| **Accept edits** (`acceptEdits`) | Changes files inside your project folder. It also does simple file jobs there, such as making, copying, moving and deleting files. | Other commands, anything outside the project folder, and protected places such as the `.git` folder. | Designing and editing your website, once you trust the plan. |
| **Auto mode** (`auto`) | A separate safety checker (a second AI) looks at each action and approves most of them for you. | It stops risky actions. Examples: a live deploy to production, sending private data out, a force push, or running a script that it just downloaded. | Long jobs when you do not want many questions. |
| **Don't ask** (`dontAsk`) | Only the actions that you approved in advance. | Nothing. Anything else is refused, not asked. | Locked-down setups. Most beginners never need it. |
| **Bypass permissions** (`bypassPermissions`) | Everything, with no checks. | Nothing. | Only a throwaway computer or virtual machine with nothing important on it. **Not for you.** |

Say this about auto mode: it **reduces** the questions. It does not make Claude safe. The checker can be wrong. Auto mode needs a supported model and account. If it is missing from your mode cycle, it is not available to you, and that is fine.

Modes and their labels can change between versions. The bottom of the screen shows the current mode. The current names are in the official guide: https://code.claude.com/docs/en/permission-modes

**Warning for day 1:** The docs say newer versions may start a terminal session in auto mode when it is available. Before the first request, ask the person to read you the exact words at the bottom of the screen. If it says auto, tell them to push `Shift` and `Tab` once, then read the words again. The first push from auto goes to Manual. Do not tell them that a missing label means Manual. Ask them to tell you what they see.

### How to switch mode

- Push `Shift` and `Tab` together. Each push moves to the next mode: Manual, then Accept edits, then Plan mode. Auto mode and Bypass permissions come after, when they are available. `dontAsk` is never in this cycle. The current mode shows at the bottom of the screen.
- Or start Claude with a mode already chosen. Example: `claude --permission-mode plan`
- Type `/permissions` to see what Claude is allowed to do and what it was blocked from doing.

### The simple recipe for beginners

1. **Day 1: stay on Manual.** Read every request. Learn what Claude does.
2. **For each new job: switch to plan mode first.** Say what you want. Read the plan. Fix it with a plain request like "Make it simpler" or "Do not change the menu". When the plan is right, approve it.
3. **When you trust the plan: switch to accept edits** for the building work. This stops the constant questions for file changes. Claude still asks before it runs other commands. Accept edits can delete files in the project, so save a checkpoint first.
4. **After a week or two, try auto mode** if it is available to you and you want fewer questions. Keep working in your project folder only.
5. **Never use bypass permissions** on a computer that holds your real files.

### Practice: plan mode, then accept edits (5 minutes)

Do not skip this. It is the habit that saves the most time and tokens. Plan mode makes Claude think first, so the person fixes the idea before any work is done. That is cheaper than building the wrong thing and undoing it.

1. In Claude Code, push `Shift` and `Tab` until the bottom of the screen shows plan mode. Ask the person to read you the words.
2. Ask: `Plan a one-page website for my business. Do not build anything yet.`
3. Read the plan together. Ask the person to change one thing in plain words, for example "Make it shorter". Claude updates the plan.
4. Tell them: nothing was built. That is plan mode. When the plan is right, they approve it.
5. Push `Shift` and `Tab` until the bottom shows accept edits. Say: "Now Claude can change files in this folder without asking each time. It still asks before other commands."
6. Ask: `Make a file called plan-practice.md that holds this plan.` Watch it write the file with no question.
7. Push `Shift` and `Tab` back to Manual before the next lesson.

Use this loop for every new job: plan mode, fix the plan, accept edits, build.

### Auto mode and your live deploy

Auto mode blocks live deploys to production by design. If Claude refuses to run `npx vercel --prod` in Part 7, this is the reason, and nothing is broken. Run the deploy yourself. Type `! npx vercel --prod` in the prompt, or run it in a normal terminal window.

### Which model for which job

Claude comes in 3 sizes. A bigger model thinks harder and costs more. Type `/model` to choose one.

| Job | Use |
|---|---|
| Simple, repeat work with no thinking: renaming files, reformatting, copying values | **Haiku** (smallest, cheapest) |
| Clear jobs with context: research, writing, routine edits | **Sonnet** (middle) |
| Hard or unclear jobs, and planning a big change | **Opus** (largest) |

3 rules:

1. **Not sure? Choose the larger model.** Quality comes before cost.
2. **A weak answer? Do the job again one size up.**
3. **Check the work of a smaller model** before you trust it.

For the website: plan on the largest model, build on the middle one, and use the smallest only for bulk jobs such as renaming 40 photos.

## Part 5 - Design first, on an editable design board

Good websites start with a design, not with code. The person decides how the site looks and what it says. Then Claude builds exactly that in Astro. This part makes a design board: a single page where they click any text to change it, and change colours, fonts and spacing with simple controls. It saves by itself. It becomes their design partner for the whole project.

### 5a. Ask 5 design questions

Ask them one at a time. Write the answers down for the board.

1. **What is the page for?** One sentence. Example: "To get new clients to email me."
2. **Who is it for?** One kind of visitor. Example: "Small shop owners who are short of time."
3. **What is the one thing a visitor should do?** One action. Example: "Send me an email."
4. **What 3 words describe the feeling?** Examples: calm, bold, friendly, premium, playful.
5. **Which 2 or 3 websites do they like the look of?** They can paste links. Ask what they like about each.

### 5b. Teach 7 design rules in plain words

Say these in your own friendly words. Give 1 example each from the person's own site.

1. **One main job per page.** One main button. Everything else is quieter.
2. **Make the important thing biggest.** Size and space show what matters first.
3. **Use space.** Empty space is not wasted. Crowded pages feel cheap.
4. **2 fonts at most.** One for headings, one for text. Body text between 16 and 20 px.
5. **Colour: 1 brand colour, 1 accent colour, calm neutrals.** Mostly neutral, a little brand, a touch of accent.
6. **Make text easy to read.** Strong contrast (at least 4.5 to 1), short lines (about 60 characters), big buttons.
7. **Phone first.** Most visitors use a phone. Always check the phone view.

### 5c. Make the design board

First make a folder for the design. In Claude Code, ask:

```
Make a folder at ~/websites/my-site-design and move into it.
```

Now build the board. Pick the first way that works:

1. **A saved file (works for everyone).** The file `design-board-template.html` sits next to this guide. Ask Claude Code: `Copy design-board-template.html into this folder as design-board.html. Set the site name and the starting words, colours and fonts from my answers in Part 5a. Then open it in my browser.` On a Mac, Claude opens it with `open design-board.html`. On Windows, `start design-board.html`.
2. **An editable Claude artifact.** If your Claude can make artifacts (pages that show beside the chat), ask it to publish the design board as an artifact. Use the template as the base. The person edits in the artifact. **They must still use the download buttons, because the downloaded files are what move into the Astro project.**
3. **No template file (for example, you are in a chat).** Build the board from this spec in 1 HTML file, with no internet needed:
   - A preview page with these sections: menu, top banner, 3 key points, about, contact, footer. All text is click-to-edit.
   - Controls: brand, accent, background, card and text colours; heading font and body font from system fonts; text size; spacing; corner roundness; section on/off and up/down.
   - A contrast checker that shows pass or fail at 4.5 to 1.
   - A Desktop and Phone view button.
   - Autosave in the browser, plus buttons for "Download design.json", "Load design.json", "Download brief" (a markdown file) and "Copy brief".
   - The brief holds the design tokens as CSS custom properties, the sections in order and all the text, plus build rules for Astro.

### 5d. Design together

Tell the person how the board works:

- **Click any text** in the preview and type to change it.
- **Colours, fonts, size and spacing** are on the left. The page changes as they move them.
- **Contrast check** under the colours. It must say "Easy to read" for all 3 lines.
- **Phone button** at the top. Check it before they finish.
- **Sections:** switch them on or off, and move them up or down.
- It **saves by itself** in their browser. For a safe copy, push "Download design.json".

Coach them. If the banner is crowded, say: "Try fewer words. One idea per sentence." If the colours are many, say: "Keep 1 brand colour and 1 accent." Come back to the 7 rules.

When they are happy, they push **Download brief** and **Download design.json**. Both files go to their Downloads folder. Ask Claude Code: `Move design-brief.md and design.json from my Downloads folder into this folder.`

### 5e. How the design and Astro work together

Explain this once. It is the key idea.

| On the design board | In the Astro site |
|---|---|
| Colours, fonts, spacing, roundness | CSS custom properties in `src/styles/global.css` |
| Each section (menu, banner, key points...) | One component in `src/components/` |
| The text | The text inside those components and `src/pages/index.astro` |
| The order of the sections | The order in `src/pages/index.astro` |

The board is the design. Astro is the finished website. When the person wants a change, they change the board first, download the new files, and ask Claude to update Astro. This keeps the design and the site matched.

## Part 6 - Build the site with Astro, from the design

Astro is the tool that builds the website. Claude Code does most of the typing. The person decides what the site says and how it looks, and they already did that in Part 5.

### 6a. Make the project

First leave Claude Code with `/exit`. Then, in the terminal, run:

```bash
cd ~/websites
npm create astro@latest my-first-site
```

On the first run, the terminal asks "Ok to proceed? (y)". Type `y` and push Enter.

Astro asks some questions. Give these answers:

| Question | Answer |
|---|---|
| Which template? | "A basic, minimal starter" |
| Install dependencies? | Yes |
| Initialize a new git repository? | Yes |

The wording may change a little. If you are not sure, the default is almost always right. Use the arrow keys to move and Enter to choose.

On a Mac, a pop-up may ask to install "command line developer tools". Click "Install". Wait for it to end. Then run the command again.

When it ends, move into the project and bring the design in:

```bash
cd my-first-site
mkdir design
cp ~/websites/my-site-design/design-board.html ~/websites/my-site-design/design.json ~/websites/my-site-design/design-brief.md design/
```

On Windows PowerShell, ask Claude Code to copy the 3 files into the `design` folder instead.

The `design` folder is not part of the website. Astro ignores it. It is the person's design partner, kept next to the site.

### 6b. Build the design in Astro

Start Claude Code in the project. Switch to plan mode with `Shift` and `Tab` (Part 4). Then say:

```
Read design/design-brief.md. Build my website in Astro from this design.
Follow the tokens and the text exactly. Show me the plan first.
```

Read the plan with the person. When it is right, approve it. Then switch to accept edits so Claude can build without asking about every file. Ask Claude to save a checkpoint when it ends.

### 6c. See the site on your own computer

Leave Claude Code (`/exit`) or open a second terminal window. Run:

```bash
npm run dev
```

The terminal shows a web address, usually http://localhost:4321. Ask the person to open it in a browser by clicking that link. They see their site, built from their design.

This copy is private. Only they can see it. The terminal stays busy while the site runs. To stop it, type `q` and push Enter, or push `Ctrl` and `C`.

Tip: use a second terminal window for Claude Code, so the site keeps running. Open a new terminal, run `cd ~/websites/my-first-site`, then run `claude`.

### 6d. Ask Claude Code to change the site

Use the loop that keeps design and site matched:

1. Open `design/design-board.html` in a browser. On a Mac: `open design/design-board.html`.
2. Load `design/design.json` with the "Load design.json" button.
3. Change what they want. Look at the phone view.
4. Download the new `design-brief.md` and `design.json`. Put them in the `design` folder.
5. Tell Claude: `The design brief changed. Update the Astro site to match it. Show me the plan first.`

For a small text change, they can also just ask Claude Code in plain words. Examples:

- `Change the main heading to "Welcome to <their name or business>".`
- `Add an About page that says <1 or 2 lines about them>. Add a link to it in the menu.`
- `Add a contact section with the email address <their email>.`

After each change, the browser at http://localhost:4321 updates by itself. If they do not like it, they say so in plain words: `Make the text bigger.` or `Undo that last change.`

Tell them: the best habit is to ask for one change at a time and look at the result.

### 6e. What is inside the project

Give this tour once. Do not go deeper unless they ask. A new minimal project has only `src/pages` and `public`. The other folders appear when Claude builds the design.

| Path | What it is for |
|---|---|
| `src/pages/index.astro` | The home page. |
| `src/pages/about.astro` | A page called "about". Every file in `src/pages` is 1 page on the site, and the file name is the address. |
| `src/components/` | Small reusable parts, such as a menu. Each design section lives here. |
| `src/layouts/` | The shared frame that pages sit in. |
| `src/styles/global.css` | The design tokens: colours, fonts, spacing. |
| `public/` | Images and files that are used as they are. |
| `design/` | The design board and the brief. Not part of the site. |
| `astro.config.mjs` | Settings. The person almost never needs to change this. |
| `package.json` | The list of tools that the project uses. |

An `.astro` file has 2 parts. The part between the `---` lines is optional code. Everything below is the page, written in normal HTML. Show this small example:

```astro
---
const name = "Sam";
---
<h1>Hello, {name}!</h1>
<p>Welcome to my site.</p>
```

Tell them: they do not need to write this. Claude Code writes it. It helps to know what they are looking at.

### 6f. Check that the site builds

Before the site goes live, make sure it builds with no errors. Stop the dev server with `Ctrl` and `C`. Then run:

```bash
npm run build
```

They should see lines ending with a message like "Complete!". A new folder called `dist` appears. It holds the finished site. If there is an error, tell Claude Code: `I ran npm run build and got this error:` and paste the error.

## Part 7 - Put the site on the internet with Vercel

### 7a. Make a free Vercel account

1. Open https://vercel.com/signup in a browser.
2. Ask: "Will this site make money, for example a business, coaching or shop site?" If **no**, choose "Hobby". It is free, for personal projects only. If **yes**, Vercel's free Hobby plan is not allowed for commercial use, so they need a paid plan. Show them the prices at https://vercel.com/pricing and the rules at https://vercel.com/legal/terms. Do not let them pay until they understand the price and say yes. You are not a lawyer, so the terms are the final word.
3. Sign up with an email address, Google or GitHub. Check the email inbox for a confirmation message.

### 7b. Sign in to Vercel from the terminal

Use `npx`. It runs the Vercel tool without a separate install, which avoids most permission errors.

In the project folder (`my-first-site`), run:

```bash
npx vercel login
```

If the terminal asks "Ok to proceed? (y)", type `y`. Vercel then asks how to sign in. Choose the same way they signed up. A browser page opens. They confirm there and go back to the terminal. They should see "Success".

### 7c. Put the site live

Run:

```bash
npx vercel --prod
```

Vercel asks some questions. Give these answers. If the wording differs, the default answer is the safe one.

| Question | Answer |
|---|---|
| Set up and deploy? | `Y` |
| Which scope? | Choose their own account (press Enter) |
| Link to existing project? | `N` |
| What is your project's name? | Press Enter, or type a short lowercase name |
| In which directory is your code? | Press Enter (`./`) |
| Want to override the settings? | `N` |

Vercel finds Astro by itself. A static Astro site needs no extra settings. After about a minute, the terminal shows a web address that ends in `.vercel.app`. Look for the line that starts with "Production".

Ask them to open that address. **Their website is live.** Celebrate. Anyone in the world can open it now. They can also see all their projects at https://vercel.com/dashboard.

Warning: a live site is public. Do not put private information on it, such as a home address or a phone number they want to keep private.

### 7d. Change the site later

1. Change the design board if the look changes. Update the brief (Part 6d).
2. Ask Claude Code for the change.
3. Look at it at http://localhost:4321.
4. Run `npm run build`.
5. Run `npx vercel --prod` again. The same address updates.

Tip: `npx vercel` with no `--prod` makes a test copy at a different address. Vercel may ask for a Vercel login to open it. If a friend sees a Vercel sign-in page, the link was a test copy. Send the "Production" address instead.

### 7e. Next steps, when they are ready

Do not teach these now. Offer them.

- **A custom address, like `mybusiness.com`.** Open https://vercel.com/dashboard, open the project, then Settings, then Domains. Buying a domain costs money. Vercel shows the price before they buy.
- **Automatic updates with GitHub.** The site updates each time they save work to GitHub. They make an account at https://github.com/signup. Then ask Claude Code: `Help me put this project on GitHub and connect it to Vercel.`
- **More pages and features.** A blog, a gallery, a contact form. Ask Claude Code in plain words.
- **Skills.** A skill teaches Claude Code one job, such as writing in their voice. Ask Claude Code: `How do I make a skill?`

## Part 8 - Try a real project (after the site is live)

The person now knows the loop: plan mode, fix the plan, accept edits, build, check by hand. Offer these 2 projects. Let them choose 1. Both use the same loop. Do not start a project until the site is live.

### Project A: A clickable, editable report or slide deck, shared on Vercel

Use it for a client PR report, a coverage summary or a pitch deck. The result is 1 page that looks good, that they edit by clicking, that they can download as **HTML, PDF or PowerPoint**, and that anyone can open from a link.

The file `report-deck-template.html` sits next to this guide. It is tested. It is a 6-slide deck: a title, 3 key numbers, a chart that reads from a data table, what worked, next steps and a thank-you slide. All text is click-to-edit. Three buttons sit at the top: **Download HTML**, **Download PDF** and **Download PowerPoint**.

1. **Ask 3 questions.** What is the one message? Who will read it? What numbers do you have (a spreadsheet, a CSV file, or typed)?
2. **Start from the template.** In Claude Code, use this prompt and fill in the brackets:

```
Copy report-deck-template.html into this folder as report.html.
Change the slides to fit my report. The one message is: [message]. The reader is: [reader].
Use the colours and fonts from design/design-brief.md.
Put my numbers in the Data table at the top. The chart reads from that table.
Use only the data I give you. Do not invent a number. Mark anything missing as "needs data".
Keep the 3 download buttons working. Then open it in my browser.
My data: [paste it, or name the file]
```

   For a 1-page report and not a deck, add: `Make it a 1-page report layout and keep the 3 download buttons.`

   **No template file (for example, in a chat)?** Ask Claude to build 1 HTML file from this spec: click-to-edit text; a Data table that drives a chart; a "Download HTML" button that saves the page with the edits; a "Download PDF" button that opens the print window, with print styles that put 1 slide on each landscape page; and a "Download PowerPoint" button that uses the PptxGenJS library (`https://cdn.jsdelivr.net/npm/pptxgenjs@3.12.0/dist/pptxgen.bundle.js`) to make a .pptx with a native chart.
3. **Edit by clicking.** The person changes words on the page. They change numbers in the Data table, and the chart updates. Tell them: edits do not save by themselves. A download is the save.
4. **Download it.** Explain each button:
   - **Download HTML** keeps all their edits in one file. They can open it again later. This is the version for the website.
   - **Download PDF** opens the print window. They choose **Save as PDF** as the destination. If the colours are missing, they switch on "Background graphics". Each slide is 1 landscape page. A PDF is best for email.
   - **Download PowerPoint** makes `report.pptx`. It needs the internet. The chart in it is a real PowerPoint chart: they right-click it and choose Edit Data. The fonts become Georgia and Arial, so the look is close and not identical. They should open it in PowerPoint, Keynote or Google Slides and check each slide.
5. **Move it into the website.** Ask Claude Code: `Copy report.html into public/reports/q4-report.html.` If people should also download the PDF or PowerPoint, they put those files in `public/reports/` too. Everything in `public/` goes live as it is. The address will be `https://<their-site>/reports/q4-report.html`.
6. **Put it live.** Run `npx vercel --prod` (in auto mode, type `! npx vercel --prod`). Check the address in a browser.
7. **Share the link.** Warn them before they share:
   - A live page is public. Anyone with the link can open it, and search engines may find it. The template already tells search engines to skip it, but that is not security.
   - Never publish a client's private numbers. A hard-to-guess file name is not security.
   - For a page that needs a password, ask Vercel what their plan allows: https://vercel.com/docs

To change a live report: edit it by clicking, download the HTML, copy it over the old file, and run `npx vercel --prod` again.

### Project B: A database you can question, for big data sets

Use it for coverage reports, social media monitoring or GEO reports (how often AI answer tools mention or cite a brand). A spreadsheet slows down at about 100,000 rows. A database answers in seconds, and gives the same answer every time.

The tool is **SQLite**. It is free and it is 1 file. On a Mac it is already installed. SQL is the language that asks the database a question. The person does not write SQL. Claude Code does, and shows it.

1. **Make a project folder.** Ask Claude Code: `Make a folder ~/websites/data-project with a folder called data inside it. Move into it.` Put the original CSV or Excel files in `data/`. **Rule: never edit the original files.** Claude works on copies.
2. **No data yet? Practise with fake data.** Ask: `Make a fake coverage data set of 50,000 rows in data/coverage.csv. Include date, outlet, author, headline, url, reach, sentiment and campaign.` Do the same for social posts or GEO answers.
3. **Plan first (plan mode).** Say:

```
Look at the files in data/. Plan a SQLite database for them: the tables, the column types, the indexes, and how to handle dates, duplicates and blank cells.
Do not build anything yet. List what could go wrong.
```

   Read the plan together. Use the largest model for this step. A wrong design costs the most time later.
4. **Build it with a script they can run again.** Switch to accept edits. Say: `Build the database from the plan. Save the import as import.py so I can run it again when I get new data.`
5. **Check before you trust it.** Say: `Check the database and show me the results of each check.` The checks are:
   - The number of rows in each table equals the number of rows in the file.
   - `COUNT(*)` equals `COUNT(DISTINCT id)`. If not, there are duplicates.
   - The number of blank cells in each column.
   - The first and the last date. They must match what the person expects.
   - 10 random rows, checked by eye against the original file.
   - One total worked out 2 different ways. Both must agree.
   - The column names. If they read `column1`, `column2` and so on, the import lost the first row. Ask Claude to import again so that the first row becomes the names.
6. **Ask questions in plain words.** Add this rule to every question: `Show me the SQL, the result, and one separate query that checks the result.` **A number without its SQL is a guess.** If the 2 queries disagree, stop and find out why.
7. **Save good questions.** Ask Claude to keep each good query in a `queries/` folder with a clear name. Next month, the person runs them again on the new data.
8. **See the data by clicking.** DB Browser for SQLite is a free app that shows the tables like a spreadsheet: https://sqlitebrowser.org/dl/
9. **Turn the answers into a report.** Give the results to Project A: `Turn these results into a 1-page report. Use only these numbers.`

Starter tables, for Claude to start from (the columns can change):

| Use | Table | Columns |
|---|---|---|
| Coverage | `coverage` | id, published_at, outlet, author, headline, url, reach, sentiment, mentions_brand, campaign |
| Social monitoring | `social_posts` | id, posted_at, platform, author, text, likes, shares, replies, url, topic |
| GEO reporting | `geo_answers` | id, checked_at, engine, prompt, brand_mentioned, cited_url, position, competitor_mentions, answer_text |

Example questions:

- **Coverage:** Which 10 outlets gave us the most coverage each quarter? What share of the articles has positive sentiment? Which campaign gave the most reach?
- **Social:** Which day had the most mentions, and what caused the spike? Which 10 authors have the most reach? How does one platform compare with another each week?
- **GEO:** For each prompt, how often is our brand mentioned? What is our share of mentions against 3 competitors? How did that change week by week?

Rules for this project:

- **Never put the database file in `public/`.** Everything in `public/` goes live on the internet. Keep the `.db` file and the CSV files in `data-project`, not in the website.
- **Personal data.** Names and social handles are personal data. Only use data that you are allowed to use. Do not put personal data in a public report.
- **Model size.** Plan the design on the largest model. Use the smallest model only for mechanical cleaning, such as renaming columns, and check its work.
- **If it is slow.** Millions of rows or slow answers? Ask Claude Code about DuckDB, a free tool that is built for big analysis.

## When something goes wrong

First, say this to the person: "This is normal. Errors are not your fault, and they are almost always easy to fix."

### The best fix for everything

1. Select the whole error text in the terminal and copy it.
2. Open Claude Code in the project folder.
3. Type: `I ran this command: <the command>. I got this error:` Then paste the error.
4. Ask: `Please explain in simple words what went wrong and fix it.`

Claude Code reads the error, finds the cause and usually fixes it. In chat mode, paste the command and the error to the chat.

### Common problems

| Problem | What to do |
|---|---|
| `command not found: claude` | Nothing is broken. Close the terminal and open a new one. If it still fails, run `~/.local/bin/claude --version`. If that shows a version number, Claude Code is installed and the Mac only needs its search path updated. Run `echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc`, then close the terminal and open a new one. If you see "no such file", run the install command again. |
| `command not found: node` or `npm` | Node.js is not installed, or the terminal is old. Install it from https://nodejs.org. Close the terminal and open a new one. |
| `command not found: npx` on Windows, or "running scripts is disabled" | In PowerShell, type `npx.cmd vercel --prod` instead of `npx vercel --prod`. Or ask Claude Code to fix the PowerShell script setting. |
| Node.js version is too old for Astro | Install the newest LTS version from https://nodejs.org. Close the terminal and open a new one. |
| The sign-in page does not open | Copy the web address that the terminal prints. Paste it into a browser. |
| http://localhost:4321 does not load | Make sure `npm run dev` is still running in a terminal window. Make sure the terminal is in the `my-first-site` folder. |
| The design board is empty or lost its changes | Open it in the same browser as before. Or use "Load design.json" with the saved file. |
| A pop-up asks for "developer tools" on a Mac | Click "Install". Wait. Run the command again. |
| `npm run build` shows an error | Paste the error to Claude Code and ask it to fix it. |
| Vercel shows a login page to visitors | They shared a test link. Share the "Production" address. |
| Claude changed something they dislike | Push `Esc`. Type `Undo that last change.` Or ask for the last checkpoint (Part 4). |
| Claude asks too many questions | Switch to accept edits with `Shift` and `Tab` (Part 4). |
| Claude will not run the live deploy | Auto mode blocks live deploys on purpose. Type `! npx vercel --prod` in the prompt (Part 4). |
| The answer from a helper is weak | Do the job again on the next larger model (Part 4). |
| Claude did a lot before you could read it | Switch to plan mode with `Shift` and `Tab`. Ask for the plan first. |
| Claude Code seems stuck | Push `Esc`. Then give a smaller request. |
| Claude forgets what you did earlier | Type `/clear` and start a clear request. Or ask Claude to write the key facts into a file called `CLAUDE.md`. |
| Anything else | Run `claude doctor`. It checks the install. Paste its output to Claude or to the person who helps you. |

### Where to get more help

- Inside Claude Code: type `/help`, or just ask Claude Code a question in plain words.
- Claude Code guide: https://docs.claude.com/en/docs/claude-code/overview
- Astro guide: https://docs.astro.build
- Vercel guide: https://vercel.com/docs
- Vercel help: https://vercel.com/help
- The community that shared this guide. Ask there. Someone else had the same problem.

## Safety and good habits

- **Never share a password or a secret key** in a chat, a post or a public website. Vercel and Claude will never ask for your password in a prompt.
- **Read before you say yes.** Claude Code asks before it acts. If you do not understand a request, ask Claude what it means.
- **Do not use bypass permissions or `--dangerously-skip-permissions`.** They turn off the safety checks.
- **Save a checkpoint before a big change.**
- **Keep your work in one folder per project.** Start Claude Code from inside that folder.
- **Start small.** One page first. Then add more.

## How to end the session

When the site is live, give the person a short summary:

1. What they installed: Claude Code and Node.js, with the version numbers.
2. The address of their live website.
3. The commands they will use again: `claude`, `npm run dev`, `npm run build` and `npx vercel --prod`.
4. The 3 modes to remember: Manual, Plan mode and Accept edits. `Shift` and `Tab` switches them. Also the 3 model sizes: Haiku, Sonnet and Opus.
5. Where the design board is: `design/design-board.html` in the project folder.
6. The 2 projects they can try next: an editable report or deck (Project A) and a database they can question (Project B).
7. One small change to try tomorrow, for example: "Change the accent colour on the design board, then update the site."

Finish with a kind line, such as: "You designed a website, built it and put it on the internet. That is a real thing to be proud of."
