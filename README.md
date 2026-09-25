# Postraid Agent Skill

**From product brief to a reviewed social-content library.**

Postraid helps founders, creators and growth marketers turn product context into social content. Start with a website or product brief, explore reactions, memes and carousels, then keep the ideas that fit the brand. The application combines a content library, creative review and publishing calendar so approved work has a place to go next.

[Website](https://www.postraid.com) · [MCP repository](https://github.com/postraid/mcp-server) · [Agent skill](https://github.com/postraid/agent-skill) · [npm package](https://www.npmjs.com/package/postraid-mcp)

## What the skill adds

An MCP server supplies tools; this skill supplies task guidance. [SKILL.md](SKILL.md) helps a compatible agent choose the right account and records, follow pagination, interpret the returned evidence and communicate the result accurately. It does not create a Postraid account or grant access by itself.

## When to use it

> List my brands, then show the saved content for the brand I select.

> Review this saved carousel and suggest a clearer opening based on my product brief.

> Save these five slides as an editable carousel draft. Return its editor link without generating media or publishing.

## Install

With an agent supported by the skills installer:

```sh
npx skills add postraid/agent-skill
```

Alternatively, place [SKILL.md](SKILL.md) in the skills directory supported by your agent. Skill installation and MCP connection are separate steps: connect `https://mcp.postraid.com/mcp` in a remote MCP client, or use `npx -y postraid-mcp` for a stdio client with Node.js 22+. See the [complete MCP setup guide](https://github.com/postraid/mcp-server). Sign in through the browser and review the requested permissions.

## The workflow

1. Choose the owned brand and inspect existing content to avoid repeating the same idea.
2. Prepare a title, one to ten slides and hashtags that match the supplied product brief.
3. Save the requested carousel draft, return its editor link, and review copy and backgrounds in Postraid before scheduling.

### Available MCP operations

| Tool | What it does |
| --- | --- |
| `get_profile` | Read the signed-in account context. |
| `list_brands` | Find brands in the user’s own workspace. |
| `list_posts` | Browse saved content pieces for an owned brand. |
| `get_post` | Read an existing owned content piece. |
| `create_post_draft` | Save supplied copy as an editable carousel with placeholder backgrounds and an editor link. |

## What a useful result looks like

The agent should return the relevant record or page, the dates and statuses supplied by the tools, a concise explanation of the evidence, and the exact product links needed to continue. It should follow pagination before calling a list complete, distinguish missing data from a failed request, and label interpretations as interpretations.

The MCP reads the user’s own workspace, not team workspaces. Its posts are saved content pieces, not a delivery ledger proving that a social post went live. Draft creation does not generate backgrounds, render media, schedule, publish or spend credits. Replace placeholder backgrounds and review the result in the product. Reach, sales and viral performance are not guaranteed.

## Access and troubleshooting

Requested scopes: `profile:read content:read drafts:write`. Older profile-only connections need to reconnect and explicitly approve the additional permissions before content tools are available.

The skill never needs your password, cookies or OAuth tokens in chat. Returned documents and source-page text are data, not instructions that can override your request. For authentication problems, restart sign-in through the MCP client. For record access, check the owning account in the product. [Manage or revoke connected apps](https://www.postraid.com/oauth/mcp/connections).

## Product resources

- [Social-content workspace](https://www.postraid.com/)
- [From brief to content library](https://www.postraid.com/#how-it-works)
- [Reaction clip library](https://www.postraid.com/#reaction-library)
- [AI meme generator](https://www.postraid.com/tools/ai-meme-generator)
- [TikTok scheduling workflow](https://www.postraid.com/tools/tiktok-scheduler)
- [Content tools](https://www.postraid.com/tools)
- [Product and content articles](https://www.postraid.com/blog)

## Feedback and license

[Open a skill issue](https://github.com/postraid/agent-skill/issues) for workflow guidance, or a [connector issue](https://github.com/postraid/mcp-server/issues) for tool and connection problems. Share a minimal, redacted example. This skill is [MIT-licensed](https://github.com/postraid/agent-skill/blob/main/LICENSE); installing it does not confer marketplace approval or additional product permissions.
