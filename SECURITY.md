# Security Policy

The semcomhq packages are bounded MCP servers. Each one is meant to reach exactly the files, hosts, or tool calls its configuration names and nothing else. A way around that boundary is a vulnerability, and we want to hear about it privately and first.

## How to report

Do not open a public issue or pull request for a security problem, and please hold public disclosure until a fix is out.

- Preferred: open a private advisory from the affected repository's **Security** tab ("Report a vulnerability").
- Email: **security@apilify.com** (Apilify Inc. maintains these packages). Put the repository name in the subject line.

We will acknowledge your report within 3 business days, agree a disclosure timeline with you, keep you posted while the fix is in progress, and credit you in the advisory unless you ask to stay anonymous.

## What we consider a vulnerability

- `mcp-fs` reading, listing, or writing outside its configured root: traversal, symlinks, prefix confusion, encoding tricks, races, or a refused write that still changed something.
- `mcp-fetch` reaching a host that is not on its allowlist, including through redirects, DNS rebinding, userinfo tricks, alternate IP encodings, or any request that leaves before the check runs.
- `mcp-gate` letting through a tool call, environment variable, or outbound connection that its policy says to block, or a gate decision that can be influenced by the request it is deciding on.
- Any package running code at install time, or a difference between what a `PROVENANCE.md` says a vendored capability does and what the shipped bytes do.

In scope: every repository in this organization and the `@semcomhq/*` npm packages.

Out of scope: vulnerabilities in third-party dependencies (report those upstream; a heads-up to us is welcome), bugs inside a server that `mcp-gate` supervises unless the gate let it do something the policy forbids, findings that require an already compromised machine or maintainer account, and social engineering.

## Coordinated disclosure

We ask for a reasonable window to fix and release before anything is published. 90 days is our default, and we will go faster whenever we can. If the weakness also affects an upstream or downstream project, we will help coordinate disclosure with them.

## Supported versions

Security fixes land on the latest released line of each package. The advisory will say which releases a fix covers.

---

This policy is the organization default. It applies to every semcomhq repository that does not carry its own `SECURITY.md`.
